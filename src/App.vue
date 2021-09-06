<template>
  <div class="container todo-container">
    <div class="row">
      <div class="col-md-6 mx-auto border border-2 p-3 rounded-3 bg-white">
        <header>
          <my-header></my-header>
        </header>
        <main>
          <list></list>
        </main>
        <footer>
          <my-footer></my-footer>
        </footer>
      </div>
    </div>
  </div>
</template>

<script>
import { reactive, computed, provide } from "vue";
import MyHeader from "./components/Header.vue";
import List from "./components/List.vue";
import MyFooter from "./components/Footer.vue";
export default {
  name: "App",
  components: {
    MyHeader,
    List,
    MyFooter,
  },
  setup() {
    let todos = reactive([
      { title: "打一場羽毛球", finished: false },
      { title: "打一場籃球", finished: false },
      { title: "打一場乒乓球", finished: false },
      { title: "打一場棒球", finished: false },
      { title: "踢一場足球", finished: false },
    ]);

    // 給子組件使用的方法
    // 根據索引刪除數據
    const delTodoWithIndex = (index) => {
      todos.splice(index, 1);
    };
    // 添加一條對象,
    const addTodo = (todo) => {
      todos.unshift(todo);
      // todos.push(todo);
    };
    // 全選與取消全選
    const selectAllTodo = (isChecked) => {
      todos.forEach((todo) => (todo.finished = isChecked));
    };
    // 刪除已經完成的todo
    const delFinished = () => {
      // todos = todos.filter((todo) => todo.finished == false);
      for (let i = todos.length - 1; i >= 0; i--) {
        if (todos[i].finished) {
          todos.splice(i, 1);
        }
      }
    };

    // 發布
    provide("todos", todos);
    provide("delTodoWithIndex", delTodoWithIndex);
    provide("addTodo", addTodo);
    provide("selectAllTodo", selectAllTodo);
    provide("delFinished", delFinished);
  },
  // components: {
  //   MyHeader,
  //   List,
  //   MyFooter,
  // },
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
