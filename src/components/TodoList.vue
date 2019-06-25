<template>
  <b-container class="top-container">
    <b-card-group deck>
      <b-card header-tag="header">
        <h4 slot="header" class="mb-0">
          <i class="calendar check outline icon" style="color: #1976d2;"></i> Todo App
        </h4>
        <div>
          <h5>
            <u>
              <i>Today:</i>
            </u>
          </h5>
          <div v-for="(todo, index) in todos" :key="index">
            <Todo :todo="todo" @delete-todo="deleteTodo"/>
          </div>
          <div>
            <CreateTodo @create-todo="addTodo"/>
          </div>
        </div>
      </b-card>
    </b-card-group>
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

.top-container {
  background-color: #fff !important;
  margin: 15px !important;
  padding: 0 !important;
  border-radius: 5px;
  width: 400px !important;
}
</style>



