<template>
  <div>
    <h2>TODO application</h2>
    <router-link to="/" >Home</router-link>
    <AddTodo
        @add-todo="addTodo"
     />
     <select v-model="filter" >
         <option value="all">All</option>
         <option value="completed">Compeleted</option>
         <option value="not_completed">Not completed</option>
     </select>
    <hr />
    <Loader v-if="loading" />
    <TodoList 
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />
    <p v-else >No todos!</p>
  </div>
</template>

<script>

import TodoList from '@/components/TodoList';
import AddTodo from '@/components/AddTodo';
import Loader from '@/components/Loader';

export default {
  name: 'App',
  components: {
    TodoList, AddTodo, Loader
  },
  data() {
    return {
      todos: [],
      loading: true,
      filter: "all"
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => response.json())
      .then(json => {
          this.todos = json;
          this.loading = false;
      });
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(x => x.id !== id);
    },
    addTodo(newTodo) {
      this.todos.push(newTodo);
    }
  },
  computed: {
      filteredTodos(){
        if (this.filter === "all") {
            return this.todos;
        }
        else if (this.filter === "not_completed") {
            return this.todos.filter(x => !x.completed);
        }
        else if (this.filter === "completed") {
            return this.todos.filter(x => x.completed);
        }
      }
  }
//   ,  watch: {
//       //creating func with name of prop whick we're watching. Here it's "filter" property
//       filter(value) {

//       }
  //}
}
</script>