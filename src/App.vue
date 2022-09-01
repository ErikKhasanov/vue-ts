<template>
  <div>
    <h1>Todo List</h1>
    <input type="text" v-model="text">
    <button v-on:click="addTodo">Add</button>
    <hr>
  </div>
  <TodoList
      v-bind:todos="todos"
      v-on:toggleTodo="toggleTodo"
      v-on:removeTodo="removeTodo"
  />
</template>

<script>
import TodoList from '@/components/TodoList';

export default {
  name: 'App',
  components: {
    TodoList
  },
  data () {
    return {
      todos: [],
      text: ''
    };
  },
  mounted () {
    fetch( 'https://jsonplaceholder.typicode.com/todos' )
    .then( response => response.json() )
    .then( json => this.todos = json );
  },
  methods: {
    toggleTodo ( index ) {
      this.todos[index - 1].completed = !this.todos[index - 1].completed;
    },
    removeTodo ( id ) {
      this.todos = this.todos.filter( ( todo ) => todo.id !== id );
    },
    addTodo () {
      this.todos.push( {
        title: this.text,
        id: new Date(),
        completed: false
      } );
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2C3E50;
  margin-top: 60px;
}
</style>
