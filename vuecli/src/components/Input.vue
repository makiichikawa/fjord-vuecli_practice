<template>
  <v-container fluid>
    <v-textarea v-model='memo'
      name="memo"
      label="memo"
      value=prevMemo
    ></v-textarea>
  </v-container>
</template>

<script>
export default {
  name: 'Input',
  props: ['prevMemo'],
  computed: {
    memo: {
      get() {
        return this.$props.prevMemo
      },
      set(value) {
        this.$emit('memo', value)
      }
    }
  }
}
</script>
