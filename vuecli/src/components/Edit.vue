<template>
  <v-card>
    <v-container>
      <v-row>
        <v-col cols='2'>
          <Tasks v-bind:memos='memos' />
        </v-col>
        <v-col cols='10'>
          <Input v-on:memo='setMemo'/>
          <Button action='edit' v-on:flags='takeOver'/>
          <Button action='del' v-on:flags='takeOver'/>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
import Button from './Button.vue'
import Tasks from './Tasks.vue'
import Input from './Input.vue'

export default {
  name: 'Edit',
  props: ['memos'],
  components: {
    Button,
    Tasks,
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
    takeOver(flags) {
      if (flags.editFlag) {
        this.$emit('processing',{action: 'edit', memo: this.memo})
      }
    }
  }
}
</script>
