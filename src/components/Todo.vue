<template>
  <!-- Show todo item if isEditing = false -->
  <div class="todo">
    <div v-show="!isEditing" class="todo-content">
      <span
        class="material-icon"
        v-show="!showDoneIcon"
        @click="deleteTodo(todo)"
        @mouseover="toggleStatusIcon"
      >
        <vue-material-icon name="radio_button_unchecked" :size="22"></vue-material-icon>&nbsp;
      </span>
      <span
        class="material-icon"
        v-show="showDoneIcon"
        style="color: #1976d2;"
        @click="deleteTodo(todo)"
      >
        <vue-material-icon name="check_circle" :size="22"></vue-material-icon>&nbsp;
      </span>
      <span @click="showEditForm">{{ todo.title }}</span>
    </div>

    <div v-show="isEditing">
      <h5>
        <i class="pencil alternate icon"></i>
        <i>Edit Todo</i>
      </h5>
      <div class="ui icon input">
        <input type="text" v-model="todo.title">
        <i class="tags icon"></i>
      </div>
      <br>
      <div class="ui icon input">
        <input type="text" v-model="todo.description">
        <i class="tags icon"></i>
      </div>
      <div class="todo-options">
        <button @click="hideEditForm" class="ui primary button">Save</button>&nbsp;
        <span @click="hideEditForm" class="btn-cancel">Cancel</span>
      </div>
    </div>
    <hr class="break-line">
  </div>
</template>

<script>
export default {
  props: {
    todo: Object
  },
  data() {
    return {
      isEditing: false,
      showDoneIcon: false
    };
  },
  methods: {
    showEditForm() {
      this.isEditing = true;
    },
    hideEditForm() {
      this.isEditing = false;
    },
    deleteTodo(todo) {
      this.$emit("delete-todo", todo);
    },
    toggleStatusIcon() {
      this.showDoneIcon = !this.showDoneIcon;
    }
  }
};
</script>

<style>
.btn-cancel:hover {
  text-decoration: underline;
  cursor: pointer;
}

hr.break-line {
  border-top: 0.5px solid #eee;
}

.todo {
  margin-left: 10px !important;
}

.todo-content {
  margin-bottom: 3.5px !important;
}
</style>


