<template>
    <div class="todo-form">
      <input type="text" v-model="title" placeholder="Add a new todo" @keyup.enter="addTodo" />
      <button @click="addTodo">Add</button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TodoForm',
    data() {
      return {
        title: ''
      };
    },
    methods: {
      addTodo() {
        if (this.title.trim()) {
          this.$emit('add-todo', this.title);
          this.title = '';
        }
      }
    }
  }
  </script>
  
  <style scoped>
  .todo-form {
    display: flex;
    justify-content: center;
    margin: 1rem 0;
  }
  input {
    padding: 0.5rem;
    font-size: 1rem;
    flex: 1;
    margin-right: 0.5rem;
  }
  button {
    padding: 0.5rem 1rem;
    font-size: 1rem;
    background-color: #007bff;
    color: white;
    border: none;
    cursor: pointer;
  }
  button:hover {
    background-color: #0056b3;
  }
  </style>
  