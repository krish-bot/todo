<template>
  <div id="app">
    <Todo v-bind:todos = "todos"></Todo>
  </div>
</template>

<script>
import Todo from './components/task'

export default {
  name: 'App',
  components: {
    Todo
  },
   data() {
    return {
      todos: [
        {
          id: 1,
          title: "Learn Vue JS",
          completed: true,
          time: '17:05',
          date: '29-04-2021'
        },
        {
          id: 2,
          title: "Watch netflix",
          completed: true,
          time: '17:05',
          date: '29-04-2021'
        },
        {
          id: 3,
          title: "Go shopping",
          completed: false,
          time: '17:05',
          date: '29-04-2021'
        },
        {
          id: 4,
          title: "Learn guitar",
          completed: false,
          time: '17:05',
          date: '29-04-2021'
        },
        {
          id: 5,
          title: "Send email",
          completed: false,
          time: '17:05',
          date: '29-04-2021'
        },
      ],
    };
   }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
