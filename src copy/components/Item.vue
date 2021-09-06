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
export default {
  name: "Item",
  props: {
    todo: Object,
    delTodo: Function,
    index: Number,
  },
  data() {
    return {
      // false是隱藏，true是顯示
      isShowDelBtn: false,
    };
  },
  methods: {
    dealShow(isShow) {
      // 1. 控制按鈕得顯示和隱藏
      this.isShowDelBtn = isShow;
    },
    delItem() {
      if (window.confirm("你確定刪除嗎?")) {
        this.delTodo(this.index);
      }
    },
  },
};
</script>

<style scoped>
.btn:hover {
  background: #dc3545;
  color: white;
}
</style>
