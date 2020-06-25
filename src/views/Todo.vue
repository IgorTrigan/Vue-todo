<template>
  <div id="todo">
    <h1>Todo aplication</h1>
    <router-link class="link" to="/">Home</router-link>

    <TodoList
      v-bind:todos="todos"
      v-bind:loading="loading"
      @remove-todo="removeTodo"
      @add-todo="addTodo"
    />
  </div>
</template>

<script>
import TodoList from '../components/TodoList';

export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true,
    };
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addTodo(newTodo) {
      this.todos.push(newTodo);
    },
  },
  mounted() {
    setTimeout(() => {
      fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
        .then((response) => response.json())
        .then((json) => (this.todos = json));
      this.loading = false;
    }, 1000);
  },
  components: {
    TodoList,
  },
};
</script>
<style scoped>
.link {
  text-decoration: none;
  color: black;
  border: 1px solid black;
  padding: 5px;
  border-radius: 5px;
  box-shadow: 0 0 2px;
  margin-bottom: 25px;
}
</style>
