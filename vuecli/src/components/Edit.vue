<template>
  <v-card height='250'>
    <v-container>
      <v-row>
        <v-col cols='2'>
          <Tasks/>
        </v-col>
        <v-col cols='10'>
          <Input/>
          <Button action='edit' v-on:flags='sendFlags'/>
          <Button action='del' v-on:flags='sendFlags'/>
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
  components: {
    Button,
    Tasks,
    Input
  },
  methods: {
    sendFlags(flags) {
      this.$emit('flags', flags)
    }
  }
}
</script>
