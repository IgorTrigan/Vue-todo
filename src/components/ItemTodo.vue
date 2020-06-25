<template>
  <li class="liStyle">
    <span v-bind:class="{ done: todo.completed }">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed" />
      <strong>{{ this.index + 1 }}</strong>
      {{ todo.title }}
    </span>
    <button @click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  name: 'ItemTodo',
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
};
</script>

<style scoped>
li {
  display: flex;
  justify-content: space-between;
  border-top: 1px solid #ccc;
  padding: 15px;
}
button {
  border-radius: 50%;
  color: #ccc;
  background: red;
  border: none;
}
input {
  margin-right: 10px;
}
.done {
  text-decoration: line-through;
}
</style>
