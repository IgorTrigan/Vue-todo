<template>
  <div class="todoList">
    <h2>Todo List</h2>
    <hr />
    <div class="chooseFilter">
      <p>Choose filter:</p>
      <select v-model="filter">
        <option value="all">All</option>
        <option value="completed">Completed</option>
        <option value="not-completed">Not completed</option>
      </select>
    </div>

    <AddTodo @add-todo="addTodo" />
    <loader v-if="loading" />
    <ul>
      <ItemTodo
        v-for="(todo, i) of filteredTodos"
        :index="i"
        v-bind:key="todo.id"
        v-bind:todo="todo"
        @remove-todo="removeTodo"
      />
      <p v-if="!filteredTodos.length">There no todo !</p>
    </ul>
  </div>
</template>

<script>
import ItemTodo from '../components/ItemTodo';
import AddTodo from '../components/AddTodo';
import Loader from '../components/Loader';
export default {
  name: 'TodoList',
  methods: {
    removeTodo(id) {
      this.$emit('remove-todo', id);
    },
    addTodo(newTodo) {
      this.$emit('add-todo', newTodo);
    },
  },
  data() {
    return {
      filter: 'all',
    };
  },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos;
      }
      if (this.filter === 'completed') {
        return this.todos.filter((t) => t.completed);
      }
      if (this.filter === 'not-completed') {
        return this.todos.filter((t) => !t.completed);
      }
    },
  },

  props: ['todos', 'loading'],
  components: {
    ItemTodo,
    AddTodo,
    Loader,
  },
};
</script>

<style scoped>
hr {
  margin: 0;
  padding: 0;
}
.todoList {
  width: 600px;
  border: 1px solid #ccc;
  box-sizing: border-box;
  margin-top: 15px;
}
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
.chooseFilter {
  margin-left: 1rem;
  display: flex;
  align-items: center;
  height: 25px;
}
.chooseFilter select {
  margin-left: 1rem;
}
</style>
