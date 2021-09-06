<template>
  <div class="todo-footer">
    <div class="d-flex flex-row justify-content-between ps-2">
      <div class="form-check">
        <input
          type="checkbox"
          name=""
          id=""
          class="form-check-input"
          v-model="isChecked"
        />
        <span>已完成{{ finishedCount }}件／總計{{ todos.length }}件</span>
      </div>
      <button class="btn btn-warning btn-sm text-white" @click="delFinished">
        清除已完成任務
      </button>
    </div>
  </div>
</template>

<script setup>
import { inject, computed } from "vue";

const todos = inject("todos");
const selectAllTodo = inject("selectAllTodo");
const delFinished = inject("delFinished");

const finishedCount = computed(() => {
  return todos.reduce((total, todo) => {
    return total + (todo.finished ? 1 : 0);
  }, 0);
});
const isChecked = computed({
  get() {
    return finishedCount.value === todos.length && todos.length > 0;
  },
  set(value) {
    selectAllTodo(value);
  },
});
//   computed: {
//     finishedCount() {
//       return this.todos.reduce((total, todo) => {
//         return total + (todo.finished ? 1 : 0);
//       }, 0);
//     },
//     isChecked: {
//       get() {
//         return (
//           this.finishedCount === this.todos.length && this.todos.length > 0
//         );
//       },
//       set(value) {
//         this.selectAllTodo(value);
//       },
//     },
//   },
// };
</script>

<style scoped>
</style>
