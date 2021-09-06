<template>
  <div class="todo-main py-3">
    <ul class="list-group">
      <item
        v-for="(todo, index) in todos"
        :key="todo"
        :index="index"
        :todo="todo"
        :delTodo="delTodo"
      ></item>
    </ul>
  </div>
</template>

<script>
import Item from "./Item.vue";
export default {
  name: "List",
  props: {
    todos: Array,
    delTodo: Function,
  },
  data() {
    return {};
  },
  components: {
    Item,
  },
};
</script>

<style scoped>
</style>
