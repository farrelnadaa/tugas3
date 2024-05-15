<template>
  <div id="app">
    <Header />
    <TodoForm @add-todo="addTodo" />
    <TodoList
      :todos="todos"
      @toggle-todo="toggleTodo"
      @remove-todo="removeTodo"
      @update-todo="updateTodo"
    />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import TodoForm from './components/TodoForm.vue';
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    Header,
    TodoForm,
    TodoList,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(title) {
      this.todos.push({
        id: Date.now(),
        title,
        completed: false,
      });
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
    removeTodo(todo) {
      this.todos = this.todos.filter(t => t.id !== todo.id);
    },
    updateTodo(todo, newTitle) {
      todo.title = newTitle;
    },
  },
};
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
