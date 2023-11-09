<template>
  <TodoItems v-for="todo in todos" v-bind:key="todo" v-bind:todoProps="todo" />
</template>

<script>
import { ref } from "vue";
import TodoItems from "./TodoItems.vue";
export default {
  components: { TodoItems },
  setup() {
    const todos = ref([
      {
        id: 1,
        title: "Viec 1",
        completed: true,
      },
      {
        id: 2,
        title: "Viec 2",
        completed: false,
      },
      {
        id: 3,
        title: "Viec 3",
        completed: false,
      },
    ]);
    return { todos };
  },
};
</script>

<style></style>
