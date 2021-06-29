<template>
  <button v-on:click="click(action)">{{actionNames(action)}}</button>
</template>

<script>
export default {
  name: 'Button',
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
    click(action) {
      this.$emit('clickedAction', action)
    }
  }
}
</script>
