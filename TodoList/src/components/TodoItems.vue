<template>
  <p>
    <input type="checkbox" name="" id="" />
    {{ todoProps.title }}
    <button class="del-btn">Delete</button>
  </p>
</template>

<script>
export default {
  props: ["todoProps"],
};
</script>

<style></style>
