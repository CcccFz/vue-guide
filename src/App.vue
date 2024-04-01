<script setup lang="ts">
import { ref, computed, onMounted, onUpdated } from 'vue'

import TodoList from './TodoList.vue'

const cnt = ref(0)
const ifFlag = ref(true)

function incr() {
  cnt.value++
}

function reduce() {
  cnt.value--
}

const isPositive = computed(() => {
  return cnt.value >= 0 ? '正数' : '负数'
})

function isPositive1() {
  return cnt.value >= 0 ? '正数' : '负数'
}

onMounted(() => {
  console.log('The init count is: 0')
})

onUpdated(() => {
  console.log(`The init count is: ${cnt.value}`)
})
</script>

<template>
  <div>The count is: {{ cnt }}, is {{ isPositive1() }}</div>
  <div>The count is: {{ cnt }}, is {{ isPositive }}</div>
  <button @click="incr">+</button>
  <button @click="reduce">-</button>
  <div>
    <div v-if="ifFlag">Vue is good !</div>
    <div v-else>Oh no !!!</div>
    <button @click="ifFlag = !ifFlag">Toggle</button>
  </div>

  <TodoList></TodoList>
</template>
