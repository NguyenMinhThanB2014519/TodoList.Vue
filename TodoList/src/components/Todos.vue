<template>
  <todoItems
    v-for="todo in todos"
    v-bind:key="todo"
    v-bind:todoProps="todo"
    @item-completed="markCompleted"
    @item-delete="deleteItem"
  />
</template>

<script>
import { ref } from 'vue'
import todoItems from './TodoItems.vue'
export default {
  components: { todoItems },
  setup() {
    const todos = ref([
      {
        id: 1,
        title: 'Viec 1',
        completed: true,
      },
      {
        id: 2,
        title: 'Viec 2',
        completed: false,
      },
      {
        id: 3,
        title: 'Viec 3',
        completed: false,
      },
    ])

    const markCompleted = id => {
      todos.value = todos.value.map(todo => {
        if (todo.id === id) {
          todo.completed = !todo.completed
        }
        return todo
      })
    }
    const deleteItem = id => {
      todos.value = todos.value.filter(todo => {
        return todo.id !== id
      })
    }

    return {
      todos,
      markCompleted,
      deleteItem,
    }
  },
}
</script>

<style></style>
