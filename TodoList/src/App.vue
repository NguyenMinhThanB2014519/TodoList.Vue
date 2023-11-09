<template>
  <Header />
  <Todos />
</template>

<script>
import Header from "./components/Header.vue";
import Todos from "./components/Todos.vue";
export default {
  name: "app",
  components: { Header, Todos },
};
</script>

<style></style>
