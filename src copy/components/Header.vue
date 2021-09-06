<template>
  <div class="todo-header">
    <input
      type="text"
      class="form-control"
      placeholder="請輸入今天的任務清單，並按下Enter"
      v-model.trim="title"
      @keyup.enter="addItem"
    />
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      title: "",
    };
  },
  props: {
    addTodo: Function,
  },
  methods: {
    // 添加一條數據
    addItem() {
      const title = this.title.trim();
      if (!title) {
        alert("輸入的任務不能為空");
        return false;
      }

      let todo = { title, finished: false };
      this.addTodo(todo);
      this.title = "";
    },
  },
};
</script>

<style scoped>
</style>
