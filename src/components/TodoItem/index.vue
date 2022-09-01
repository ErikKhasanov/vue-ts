<template>
  <li v-bind:class="{done: todo.completed}">
    <span class="checkbox">
      <input type="checkbox" :checked="todo.completed" v-on:click="$emit('toggleTodo', index)">
      <strong>{{ index }}</strong>
    </span>
    <span class="title">{{ todo.title }}</span>
    <button v-on:click="$emit('removeTodo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo', 'index'],
};
</script>

<style scoped>
.title {
  margin-left: 10px;
  margin-right: auto;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 7px 0;
  border: 1px solid #2C3E50;
  padding: 7px 10px;
}

.done .title {
  text-decoration: line-through;
}

.checkbox {
  display: flex;
  align-items: center;
}

.checkbox strong {
  font-size: 12px;
}
</style>