<template>
  <li
    class="list-group-item list-group-item-action d-flex"
    @mouseenter="dealShow(true)"
    @mouseleave="dealShow(false)"
  >
    <div class="form-check">
      <input
        type="checkbox"
        class="form-check-input"
        v-model="todo.finished"
      /><label for="" class="form-check-label">{{ todo.title }}</label>
    </div>
    <button
      class="btn btn-warning btn-sm ms-auto"
      v-show="isShowDelBtn"
      @click="delItem"
    >
      刪除
    </button>
  </li>
</template>

<script>
import { ref, inject } from "vue";
export default {
  name: "Item",
  props: {
    todo: Object,
    index: Number,
  },
  setup(props, context) {
    let isShowDelBtn = ref(false);
    const delTodo = inject("delTodoWithIndex");
    const dealShow = (isShow) => {
      // 1. 控制按鈕得顯示和隱藏
      isShowDelBtn.value = isShow;
    };
    const delItem = () => {
      if (window.confirm("你確定刪除嗎?")) {
        delTodo(props.index);
      }
    };

    return { isShowDelBtn, dealShow, delItem };
  },
};
</script>

<style scoped>
.btn:hover {
  background: #dc3545;
  color: white;
}
</style>
