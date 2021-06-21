<template>
  <div>
    <div v-for='(todo, index) in todos' :key='index'>
      <p>{{ todo }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tasks',
  data: function(){
    return {
      todos: ['task1', 'task2'],
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
