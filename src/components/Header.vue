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
import { ref, inject } from "vue";
export default {
  name: "Header",
  setup() {
    let title = ref("");
    const addTodo = inject("addTodo");

    // 添加一條數據
    const addItem = () => {
      const newTitle = title.value;
      if (!newTitle) {
        alert("輸入的任務不能為空");
        return false;
      }
      let todo = { title: newTitle, finished: false };
      addTodo(todo);
      title.value = "";
    };
    return { title, addItem };
  },
};
</script>

<style scoped>
</style>
