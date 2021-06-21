<template>
  <button v-on:click="onFlag(action)">{{actionNames(action)}}</button>
</template>

<script>
export default {
  name: 'Button',
  data: function() {
    return {
      flags: { addFlag: false, editFlag: false, deleteFlag: false }
    }
  },
  props: ['action'],
  methods: {
    actionNames(action){
      const names =
      {
        add: '追加',
        edit: '編集',
        del: '削除'
      }
      return names[action]
    },
    onFlag(action) {
      switch(action) {
        case 'add':
          this.flags.addFlag = true
          break
        case 'edit':
          this.flags.editFlag = true
          break
        case 'del' :
          this.flags.deleteFlag = true
          break
      }
      this.$emit('flags', this.flags)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
