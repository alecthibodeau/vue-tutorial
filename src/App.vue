<script setup lang="ts">
import { ref } from 'vue';

const count = ref(0);

function increment() {
  // update component state
  count.value += 1;
}
</script>

<template>
  <!-- make this button work -->
  <button @click="increment">count is: {{ count }}</button>
</template>
