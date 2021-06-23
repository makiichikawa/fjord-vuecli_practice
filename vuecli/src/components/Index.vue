<template>
  <v-card>
    <v-container>
      <v-row>
        <v-col cols='2'>
          <Tasks v-bind:memos='memos' />
          <Button action='add' v-on:flags='sendFlags'/>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
import Button from './Button.vue'
import Tasks from './Tasks.vue'

export default {
  name: 'Index',
  props: ['memos'],
  components: {
    Button,
    Tasks
  },
  methods: {
    sendFlags(flags) {
      this.$emit('flags', flags)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
