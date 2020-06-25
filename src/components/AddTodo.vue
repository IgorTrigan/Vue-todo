<template>
  <div>
    <form @submit.prevent="onSubmit">
      <input type="text" v-model="title" />
      <button type="submit">Add todo</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return { title: '' };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = { id: Date.now(), title: this.title, completed: false };
        this.$emit('add-todo', newTodo);
        this.title = '';
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  height: 30px;
}
input {
  margin: 0;
  padding: 0;
  flex: 1 1 auto;
  padding-left: 10px;
}
</style>
