<template>
    <li :class="{ completed: todo.completed }">
      <input type="checkbox" v-model="todo.completed" @change="toggleTodo(todo)" />
      <span @dblclick="editMode = true" v-if="!editMode">{{ todo.title }}</span>
      <input v-if="editMode" type="text" v-model="editTitle" @keyup.enter="updateTodo" @blur="updateTodo" />
      <button @click="removeTodo(todo)">Delete</button>
    </li>
  </template>
  
  <script>
  export default {
    name: 'TodoItem',
    props: {
      todo: Object,
    },
    data() {
      return {
        editMode: false,
        editTitle: this.todo.title,
      };
    },
    methods: {
      toggleTodo(todo) {
        this.$emit('toggle-todo', todo);
      },
      removeTodo(todo) {
        this.$emit('remove-todo', todo);
      },
      updateTodo() {
        if (this.editTitle.trim()) {
          this.$emit('update-todo', this.todo, this.editTitle);
          this.editMode = false;
        }
      },
    },
  };
  </script>
  
  <style scoped>
  li {
    display: flex;
    align-items: center;
    padding: 0.5rem;
    border-bottom: 1px solid #ddd;
  }
  .completed span {
    text-decoration: line-through;
    color: #999;
  }
  input[type="checkbox"] {
    margin-right: 1rem;
  }
  input[type="text"] {
    flex: 1;
    padding: 0.5rem;
  }
  button {
    padding: 0.5rem 1rem;
    background-color: #dc3545;
    color: white;
    border: none;
    cursor: pointer;
  }
  button:hover {
    background-color: #c82333;
  }
  </style>
  