<script setup lang="ts">
const props = defineProps({
  message: String
})
</script>

<template>
  <h2>{{ message || 'No props passed yet' }}</h2>
</template>
