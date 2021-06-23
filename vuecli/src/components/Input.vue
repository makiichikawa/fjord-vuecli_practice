<template>
  <v-container fluid>
    <v-textarea v-model='memo' v-on:mouseleave='takeOver'
      name="memo"
      label="memo"
      value="The Woodman set to work at once, and so sharp was his axe that the tree was soon chopped nearly through."
    ></v-textarea>
  </v-container>
</template>

<script>
export default {
  name: 'Input',
  data: function() {
    return {
      memo: ''
    }
  },
  methods: {
    takeOver: function() {
      this.$emit('memo', this.memo)
    }
  }
}
</script>
