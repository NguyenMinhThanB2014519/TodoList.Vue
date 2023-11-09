<template>
  <form @submit="addTodo">
    <input type="text" placeholder="Add Todo .. " v-model="title" />
    <input type="submit" value="Add Todo" @click="addTodo" />
  </form>
</template>

<script>
import { v4 as uuidv4 } from 'uuid'
import { ref } from 'vue'
export default {
  name: 'addTodo',
  setup(props, context) {
    const title = ref('')
    const addTodo = event => {
      event.preventDefault()
      if (title.value.trim() === '') {
        alert('Nhap du lieu vao')
        return
      }
      const newItem = {
        id: uuidv4(),
        title: title.value,
        completed: false,
      }
      context.emit('add-todo', newItem)
      title.value = ''
    }

    return {
      title,
      addTodo,
    }
  },
}
</script>

<style scoped>
form {
  display: flex;
}
input[type='text'] {
  flex: 10;
  padding: 5px;
}
input[type='submit'] {
  flex: 2;
}
</style>
