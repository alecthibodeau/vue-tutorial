<script setup lang="ts">
import { ref, watch } from 'vue';

const count = ref(0);
const todoId = ref(1);
const todoData = ref(null);

watch(count, (newCount) => {
  // yes, console.log() is a side effect
  console.log(`new count is: ${newCount}`);
});

watch(todoId, fetchData);

async function fetchData() {
  todoData.value = null
  const res = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
  )
  todoData.value = await res.json()
}

fetchData();
</script>

<template>
  <button @click="count += 1">Count</button>
  <p>Todo id: {{ todoId }}</p>
  <button @click="todoId += 1">Fetch next todo</button>
  <p v-if="!todoData">Loading...</p>
  <pre v-else>{{ todoData }}</pre>
</template>
