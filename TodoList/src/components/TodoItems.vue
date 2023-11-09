<template>
  <p :class="('todoItems', todoProps.completed ? 'is-completed' : '')">
    <input
      type="checkbox"
      :checked="todoProps.completed"
      @change="markItemcompleted"
    />
    {{ todoProps.title }}
    <button class="del-btn" @click="deleteTodo">Delete</button>
  </p>
</template>

<script>
export default {
  props: ['todoProps'],
  setup(props, context) {
    const markItemcompleted = () => {
      context.emit('item-completed', props.todoProps.id)
      // console.log(props.todoProps.id)
    }

    const deleteTodo = id => {
      context.emit('item-delete', props.todoProps.id)
    }
    return {
      markItemcompleted,
      deleteTodo,
    }
  },
}
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
