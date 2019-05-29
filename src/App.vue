<template>
  <div id="app">
    <TodoList :todos="todos" :updateStorage="updateStorage"/>
  </div>
</template>

<script>
import TodoList from "./components/TodoList";
export default {
  name: "app",
  data() {
    return {
      todos: []
    };
  },
  methods: {
    init() {
      chrome.storage.sync.get(({ todos }) => {
        if (!todos) return;

        console.log("get todo");
        this.todos = todos;
      });
    },
    updateStorage() {
      chrome.storage.sync.set({ todos: this.todos });
    }
  },
  components: {
    TodoList
  },
  created() {
    this.init();
  }
};
</script>
<style>
.material-icon {
  top: 3px;
  position: relative;
}
</style>
