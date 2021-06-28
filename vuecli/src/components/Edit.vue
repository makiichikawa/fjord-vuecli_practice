<template>
  <v-card>
    <v-container>
      <v-row>
        <v-col cols='2'>
          <Memo v-bind:memos='memos' v-on:index='takeOverIndex'/>
        </v-col>
        <v-col cols='10'>
          <Input v-on:memo='setMemo' v-bind:prevMemo='prevMemo'/>
          <Button action='edit' v-on:flags='takeOverFlags'/>
          <Button action='del' v-on:flags='takeOverFlags'/>
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
    takeOverFlags(flags) {
      if (flags.editFlag) {
        this.$emit('processing',{action: 'edit', memo: this.memo})
      } else if (flags.deleteFlag) {
        this.$emit('processing', {action: 'delete'})
      }
    },
    takeOverIndex(index) {
      this.$emit('index', index)
    }
  }
}
</script>
