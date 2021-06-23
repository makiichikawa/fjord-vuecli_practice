<template>
  <v-app>
    <v-container>
      <v-row>
        <v-col cols='12'>
          <Index v-bind:memos='memos' v-on:flags='setFlags'/>
        </v-col>
        <v-col cols='12'>
          <Edit v-if='flags.addFlag' v-bind:memos='memos' v-on:processing='execute'/>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
import Index from './components/Index.vue'
import Edit from './components/Edit.vue'

export default {
  name: 'App',
  data: function() {
    return {
      flags: {},
      memos: []
    }
  },
  mounted() {
    if (localStorage.getItem('memos')) {
      this.memos = JSON.parse(localStorage.getItem('memos'))
    }
  },
  components: {
    Index,
    Edit
  },
  methods: {
    setFlags(flags) {
      this.flags = flags
    },
    execute(processing){
      if (processing.action === 'edit') {
        this.memos.push(processing.memo)
      }
      const parsed = JSON.stringify(this.memos)
      localStorage.setItem('memos', parsed)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
