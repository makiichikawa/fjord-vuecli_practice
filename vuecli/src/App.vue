<template>
  <v-app>
    <v-container>
      <v-row>
        <v-col cols='12'>
          <Index v-on:flags='setFlags'/>
        </v-col>
        <v-col cols='12'>
          <Edit v-if='flags.addFlag'/>
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
      flags: {}
    }
  },
  components: {
    Index,
    Edit
  },
  methods: {
    setFlags(flags) {
      this.flags = flags
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
