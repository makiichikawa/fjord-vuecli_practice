<template>
  <div>
    <div v-for='(memo, index) in memos' :key='index'>
      <p>{{ memo }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tasks',
  props: ['memos']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
