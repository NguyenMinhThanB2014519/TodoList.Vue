<template>
  <addTodo @add-todo="addItem" />
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
import { v4 as uuidv4 } from 'uuid'
import addTodo from './addTodo.vue'
import todoItems from './TodoItems.vue'
export default {
  components: { todoItems, addTodo },
  setup() {
    const todos = ref([
      {
        id: uuidv4(),
        title: 'Viec 1',
        completed: true,
      },
      {
        id: uuidv4(),
        title: 'Viec 2',
        completed: false,
      },
      {
        id: uuidv4(),
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

    const addItem = newItem => {
      todos.value.push(newItem)
    }

    return {
      todos,
      markCompleted,
      deleteItem,
      addItem,
    }
  },
}
</script>

<style></style>
