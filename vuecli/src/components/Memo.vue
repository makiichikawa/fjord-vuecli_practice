<template>
  <div>
    <div v-for='(memo, index) in memos' :key='index'>
      <p>{{ memo }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Memo',
  props: ['memos']
}
</script>
