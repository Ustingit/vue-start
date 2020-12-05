<template>
  <div id="app">
    <h1>TODO application</h1>
    <hr />
    <TodoList 
      v-bind:todos="todos"
    />
  </div>
</template>

<script>

import TodoList from '@/components/TodoList';

export default {
  name: 'App',
  components: {
    TodoList
  },
  data() {
    return {
      todos: [
        { id: 1, text: "Купить хлеб", completed: false },
        { id: 2, text: "Купить масло", completed: false },
        { id: 3, text: "Купить сыр", completed: true }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
