<template>
  <div id="app">
    <h1>To do</h1>
    <hr>

    <Todos></Todos>
  </div>
</template>

<script>
import Todos from './views/Todos.vue'

export default {
  name: 'App',
  components: {
    Todos,
  }
}
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
