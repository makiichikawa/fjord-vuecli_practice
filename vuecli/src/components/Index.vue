<template>
  <v-card>
    <v-container>
      <v-row>
        <v-col cols='2'>
          <Memo v-bind:memos='memos' v-on:index='takeOverIndex'/>
          <Button action='add' v-on:clickedAction='takeOverProcess'/>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
import Button from './Button.vue'
import Memo from './Memo.vue'

export default {
  name: 'Index',
  props: {
    memos: {},
    index: null
  },
  components: {
    Button,
    Memo 
  },
  methods: {
    takeOverProcess(action) {
      if (action === 'add') {
        this.$emit('processing', {action: 'add'})
      }
    },
    takeOverIndex(index) {
      this.$emit('index', index)
    }
  }
}
</script>
