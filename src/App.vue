<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'

import TodoList from './TodoList.vue'

const cnt = ref(0)
const isGood = ref(true)

const input = ref<HTMLInputElement | null>(null)

const isPositive = computed(() => {
  return cnt.value > 0 ? '正数' : '非正数'
})
function isPositive1() {
  return cnt.value > 0 ? '正数' : '非正数'
}

function add() {
  cnt.value++
}
function reduce() {
  cnt.value--
}

onMounted(() => {
  input.value?.focus()
})

</script>

<template>
  <div>The count is: {{ cnt }}, is {{ isPositive }}</div>
  <div>The count is: {{ cnt }}, is {{ isPositive1() }}</div>
  <div>
    <button @click="add">+</button>
    <button @click="reduce">-</button>
  </div>
  <span v-if="isGood">Vue is good!</span>
  <span v-else>oh no, Bad!!!</span>
  <button @click="isGood = !isGood">Toggle</button>
  <TodoList />

  <input ref="input">
</template>
