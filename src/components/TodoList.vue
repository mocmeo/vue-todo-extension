<template>
  <b-container>
    <h4>VueJS Todo Extension</h4>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <Todo :todo="todo" @delete-todo="deleteTodo"/>
      </li>
    </ul>

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
  props: ["todos"],
  data() {
    return {
      isCreating: false
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    },
    deleteTodo(todo) {
      let todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    }
  }
};
</script>

<style>
.add-todo {
  margin: 15px;
}

.add-todo:hover {
  color: #ff9800;
  cursor: pointer;
}
</style>


