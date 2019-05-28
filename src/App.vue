<template>
  <div id="app">
    <TodoList :todos="todos"/>
  </div>
</template>

<script>
import TodoList from "./components/TodoList";
export default {
  name: "app",
  data() {
    return {
      todos: [
        {
          title: "Todo A",
          description: "For project A",
          done: true
        },
        {
          title: "Todo B",
          description: "For project B",
          done: false
        },
        {
          title: "Todo C",
          description: "For project C",
          done: false
        }
      ]
    };
  },
  components: {
    TodoList
  }
};
</script>
<style>
</style>
