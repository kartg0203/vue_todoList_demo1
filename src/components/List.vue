<template>
  <div class="todo-main py-3">
    <ul class="list-group">
      <item
        v-for="(todo, index) in todos"
        :key="todo"
        :index="index"
        :todo="todo"
      ></item>
    </ul>
  </div>
</template>

<script>
import { inject } from "vue";
import Item from "./Item.vue";
export default {
  name: "List",
  setup() {
    const todos = inject("todos");

    return { todos };
  },
  components: {
    Item,
  },
};
</script>

<style scoped>
</style>
