<template>
    <ul>
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @toggle-todo="toggleTodo"
        @remove-todo="removeTodo"
        @update-todo="updateTodo"
      />
    </ul>
  </template>
  
  <script>
  import TodoItem from './TodoItem.vue';
  
  export default {
    name: 'TodoList',
    components: {
      TodoItem,
    },
    props: {
      todos: Array,
    },
    methods: {
      toggleTodo(todo) {
        this.$emit('toggle-todo', todo);
      },
      removeTodo(todo) {
        this.$emit('remove-todo', todo);
      },
      updateTodo(todo, newTitle) {
        this.$emit('update-todo', todo, newTitle);
      },
    },
  };
  </script>
  
  <style scoped>
  ul {
    list-style: none;
    padding: 0;
  }
  </style>
  