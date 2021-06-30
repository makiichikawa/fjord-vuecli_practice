<template>
  <v-card>
    <v-card-subtitle>編集</v-card-subtitle>
    <v-container>
      <v-row>
        <v-col cols='2'>
          <Memo v-bind:memos='memos' v-on:index='takeOverIndex'/>
        </v-col>
        <v-col cols='10'>
          <Input v-on:memo='setMemo' v-bind:prevMemo='prevMemo'/>
          <Button action='edit' v-on:clickedAction='takeOverProcess'/>
          <Button action='del' v-on:clickedAction='takeOverProcess'/>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
import Button from './Button.vue'
import Memo from './Memo.vue'
import Input from './Input.vue'

export default {
  name: 'Edit',
  props: ['memos', 'prevMemo'],
  components: {
    Button,
    Memo,
    Input
  },
  data: function() {
    return {
      memo: '',
    }
  },
  methods: {
    setMemo(memo) {
      this.memo = memo
    },
    takeOverProcess(action) {
      if (action === 'edit') {
        this.$emit('processing',{action: 'edit', memo: this.memo})
      } else if (action === 'del') {
        this.$emit('processing', {action: 'delete'})
      }
    },
    takeOverIndex(index) {
      this.$emit('index', index)
    }
  }
}
</script>
