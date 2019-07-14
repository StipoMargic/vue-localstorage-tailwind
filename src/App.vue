<template>
  <div id="app">
    <Todos></Todos>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import "./assets/css/main.css";

export default {
  name: "app",
  components: {
    Todos
  }
};
</script>

<style>
</style>
