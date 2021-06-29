<template>
  <v-list dense>
    <v-list-item-group color="pink">
      <v-list-item
        v-for="(memo, i) in memos"
        :key="i"
      >
        <v-list-item-content v-on:click="takeOver(i)">
          <v-list-item-title v-text="title(memo)"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      </v-list-item-group>
  </v-list>
</template>

<script>
export default {
  name: 'Memo',
  props: ['memos'],
  methods: {
    title(memo) {
      return memo.split(/\n/)[0]
    },
    takeOver(memoIndex) {
      this.$emit('index', memoIndex)
    }
  }
}
</script>
