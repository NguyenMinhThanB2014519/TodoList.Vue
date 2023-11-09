<template>
  <p :class="('todoItems', todoProps.completed ? 'is-completed' : '')">
    <input type="checkbox" :checked="todoProps.completed" />
    {{ todoProps.title }}
    <button class="del-btn">Delete</button>
  </p>
</template>

<script>
export default {
  props: ["todoProps"],
};
</script>

<style>
.todoItems {
  background: #f4f4f4;
  padding: 10px;
  margin: 0;
  border-bottom: 1px #ccc dotted;
}
.del-btn {
  background: red;
  color: white;
  border: none;
  cursor: pointer;
  float: right;
}
.is-completed {
  text-decoration: line-through;
}
</style>
