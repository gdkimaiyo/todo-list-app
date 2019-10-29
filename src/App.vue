<template>
  <div id="app">
    <top-bar />
    <todo-list />
  </div>
</template>

<script>
import TopBar from "./components/TopBar.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "app",

  components: {
    TopBar,
    TodoList
  }
};
</script>

<style>
</style>
