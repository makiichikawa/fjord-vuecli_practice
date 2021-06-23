<template>
  <v-card>
    <v-container>
      <v-row>
        <v-col cols='2'>
          <Memo v-bind:memos='memos' />
          <Button action='add' v-on:flags='sendFlags'/>
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
  props: ['memos'],
  components: {
    Button,
    Memo 
  },
  methods: {
    sendFlags(flags) {
      this.$emit('flags', flags)
    }
  }
}
</script>
