<template>
  <v-app>
    <v-container>
      <v-row>
        <v-col cols='12'>
          <Index v-bind:memos='memos' v-on:processing ='executeButtonProcess'  v-on:index='executeMemoProcess'/>
        </v-col>
        <v-col cols='12'>
          <Edit v-if='editFlag' v-bind:memos='memos' v-on:processing='executeButtonProcess' v-on:index='executeMemoProcess' v-bind:prevMemo='memo' />
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
      editFlag: false,
      memos: {},
      index: null,
      memo: ''
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
    executeMemoProcess(index) {
      this.index = Number(index)
      this.memo = this.memos[index]
      this.editFlag = true
    },
    executeButtonProcess(processing){
      if (processing.action === 'add') {
        this.memo = '新規メモ'
        this.memos.push(this.memo)
        this.index = this.memos.length - 1
      } else if (processing.action === 'edit') {
        this.$set(this.memos, this.index, processing.memo)
      } else if (processing.action === 'delete') {
        this.memos.splice(this.index, 1)
      }
      const parsed = JSON.stringify(this.memos)
      localStorage.setItem('memos', parsed)
      this.editFlag = false
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
