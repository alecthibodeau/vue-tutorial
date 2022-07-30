<script setup lang="ts">
import { reactive, ref } from 'vue'

// component logic
const message = ref('Hello World!');

const counter = reactive({
  count: 0
})
</script>

<template>
  <h1>{{ message.split('').reverse().join('') }}</h1>
  <div>
    <p>count is: {{ counter.count }}</p>
  </div>
</template>
