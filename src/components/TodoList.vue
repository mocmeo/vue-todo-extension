<template>
  <b-container>
    <h4>
      <i class="calendar check outline icon"></i> Todo Extension
    </h4>
    <div>
      <div v-for="(todo, index) in todos" :key="index">
        <Todo :todo="todo" @delete-todo="deleteTodo"/>
      </div>
    </div>

    <div>
      <CreateTodo @create-todo="addTodo"/>
    </div>
  </b-container>
</template>

<script>
import Todo from "./Todo";
import CreateTodo from "./CreateTodo";
import sweetalert from "sweetalert";
export default {
  components: {
    Todo,
    CreateTodo
  },
  props: {
    todos: Array,
    updateStorage: Function
  },
  data() {
    return {
      isCreating: false
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
      this.updateStorage();
      sweetalert("Created!", "Your To-Do has been created.", "success");
    },
    deleteTodo(todo) {
      let todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
      this.updateStorage();
      sweetalert("Deleted!", "Your To-Do has been deleted.", "success");
    }
  }
};
</script>
<style>
.todo-options {
  margin-top: 5px !important;
}
</style>



