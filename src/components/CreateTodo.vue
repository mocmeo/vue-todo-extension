<template>
  <div class="create-todo">
    <div v-show="!isCreating">
      <span class="add-todo" @click="openForm">
        <span style="color:#1976D2" class="material-icon">
          <vue-material-icon name="add" :size="22"/>
        </span> Add Task&nbsp;
      </span>

      <span class="add-website-todo">Add website as task</span>
    </div>

    <div v-show="isCreating">
      <h5>
        <i class="pencil alternate icon"></i>
        <i>Add Todo</i>
      </h5>
      <div class="ui icon input">
        <input type="text" v-model="title" placeholder="Title..">
        <i class="tags icon"></i>
      </div>
      <br>

      <div class="ui icon input">
        <input type="text" v-model="desc" placeholder="Description..">
        <i class="tags icon"></i>
      </div>
      <br>
      <div class="todo-options">
        <button @click="sendForm" class="ui primary button">Add</button>&nbsp;
        <span @click="closeForm" class="btn-cancel">Cancel</span>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isCreating: false,
      title: "",
      desc: "",
      done: false
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.title.length > 0 && this.desc.length > 0) {
        let title = this.title;
        let desc = this.desc;
        this.$emit("create-todo", {
          title,
          desc,
          done: false
        });
        this.title = "";
        this.desc = "";
        this.isCreating = false;
      }
    }
  }
};
</script>
<style scoped>
.add-todo:hover {
  color: #1976d2;
  cursor: pointer;
}

.add-website-todo {
  color: #1976d2;
}

.add-website-todo:hover {
  text-decoration: underline;
  cursor: pointer;
}

.create-todo {
  margin-left: 5px !important;
}
</style>

