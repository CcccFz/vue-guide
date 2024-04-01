<script setup lang="ts">
import { ref } from 'vue'

const inputTitle = ref('')
const todos = ref([])
let id = 0

function addTodo() {
  todos.value.push({ title: inputTitle.value, id: ++id })
  inputTitle.value = ''
}

function removeTodo(idx) {
  todos.value.splice(idx, 1)
  id--
}
</script>

<template>
  <div>
    <form @submit.prevent="addTodo">
      <label for="add-todo"></label>
      <input id="add-todo" v-model="inputTitle" />
      <button>New</button>
    </form>
    <ul>
      <li v-for="(todo, idx) of todos" :key="todo.id">
        {{ todo.title }}
        <button @click="removeTodo(idx)">-</button>
      </li>
    </ul>
  </div>
</template>
