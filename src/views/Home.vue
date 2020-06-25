@<template>
  <div>
    <h2>Home page</h2>
    <p>
      Here! You can see, how to work with vue.js on the exaple todo app
      (route,filters).
    </p>
    <router-link class="link" to="/todos">Todo</router-link>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.link {
  text-decoration: none;
  color: black;
  border: 1px solid black;
  padding: 5px;
  border-radius: 5px;
  box-shadow: 0 0 2px;
}
</style>
