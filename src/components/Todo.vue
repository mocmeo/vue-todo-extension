<template>
  <!-- Show todo item if isEditing = false -->
  <div>
    <div v-show="!isEditing">
      <span @click="showEditForm">{{ todo.title }}</span>
      <i class="power off icon" @click="deleteTodo(todo)"></i>
    </div>

    <div v-show="isEditing">
      <div class="ui icon input">
        <input type="text" v-model="todo.title">
        <i class="tags icon"></i>
      </div>
      <br>
      <button @click="hideEditForm" class="ui primary button">Save</button>
      <span @click="hideEditForm" class="btn-cancel">Cancel</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todo: Object
  },
  data() {
    return {
      isEditing: false
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
    }
  }
};
</script>

<style>
.btn-cancel:hover {
  text-decoration: underline;
  cursor: pointer;
}
</style>


