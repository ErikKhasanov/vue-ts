<template>
  <div class="wrapper">
    <ul>
      <TodoItem
          v-for="(todo, i) of todos"
          :key="todo.id"
          v-bind:todo="todo"
          v-bind:index="++i"
          v-on:toggleTodo="toggleTodo"
          v-on:removeTodo="removeTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem';

export default {
  name: 'TodoList',
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    toggleTodo ( id ) {
      this.$emit( 'toggleTodo', id );
    },
    removeTodo ( id ) {
      this.$emit( 'removeTodo', id );
    }
  }
};
</script>

<style scoped>
.wrapper {
  width: 360px;
  max-width: 100%;
  margin: 0 auto;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>