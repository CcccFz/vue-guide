<script setup lang="ts">
import { ref, type Ref } from 'vue'

let todoId = 0
const inputTodo = ref('')
const todos: Ref<{ id: number; title: string }[]> = ref([])

function addTodo() {
  todos.value.push({ id: todoId++, title: inputTodo.value })
  inputTodo.value = ''
}
function delTodo(idx: number) {
  todos.value.splice(idx, 1)
}
</script>

<template>
  <div>
    <form @submit.prevent="addTodo">
      <label for="add-todo"></label>
      <input id="add-todo" v-model="inputTodo" />
      <button>New</button>
      <ul>
        <li v-for="(todo, idx) of todos" :key="todo.id">
          {{ todo.title }} <button @click="delTodo(idx)">-</button>
        </li>
      </ul>
    </form>
  </div>
</template>
