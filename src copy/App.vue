<template>
  <div class="container todo-container">
    <div class="row">
      <div class="col-md-6 mx-auto border border-2 p-3 rounded-3 bg-white">
        <header>
          <my-header :addTodo="addTodo"></my-header>
        </header>
        <main>
          <list :todos="todos" :delTodo="delTodoWithIndex"></list>
        </main>
        <footer>
          <my-footer
            :todos="todos"
            :selectAllTodo="selectAllTodo"
            :delFinished="delFinished"
          ></my-footer>
        </footer>
      </div>
    </div>
  </div>
</template>

<script>
import MyHeader from "./components/Header.vue";
import List from "./components/List.vue";
import MyFooter from "./components/Footer.vue";
export default {
  name: "App",
  data() {
    return {
      todos: [
        { title: "打一場羽毛球", finished: false },
        { title: "打一場籃球", finished: false },
        { title: "打一場乒乓球", finished: false },
        { title: "打一場棒球", finished: false },
        { title: "踢一場足球", finished: false },
      ],
    };
  },
  methods: {
    // 根據索引刪除數據
    delTodoWithIndex(index) {
      this.todos.splice(index, 1);
    },
    // 添加一條對象,
    addTodo(todo) {
      this.todos.unshift(todo);
    },
    // 全選與取消全選
    selectAllTodo(isChecked) {
      this.todos.forEach((todo) => (todo.finished = isChecked));
    },
    // 刪除已經完成的todo
    delFinished() {
      this.todos = this.todos.filter((todo) => todo.finished == false);
    },
  },
  components: {
    MyHeader,
    List,
    MyFooter,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
ul {
  list-style: none;
}
</style>
