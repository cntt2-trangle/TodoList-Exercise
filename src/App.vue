<template>
  <div id="app">
    <Header />
    <TodoList />
  </div>
</template>

<script>
import Header from "./components/Header";
import TodoList from "./components/TodoList";

export default {
  name: "#app",
  components: { Header, TodoList },
};
</script>

<style>
#app {
  font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Noto Sans,
    Ubuntu, Droid Sans, Helvetica Neue, sans-serif;
  padding: 0 8px 8px 16px;
  background: #fafbfc;
}
</style>