<template>
  <div>
    <span class="add-todo" @click="openForm" v-show="!isCreating">
      <span style="color:#ff9800">+</span> Add Task
    </span>

    <div v-show="isCreating">
      <h4>Add Todo</h4>
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
      <button @click="sendForm" class="ui primary button">Add</button>
      <span @click="closeForm" class="btn-cancel">Cancel</span>
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

