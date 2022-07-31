<script setup lang="ts">
const emit = defineEmits(['response']);

/**
 * The first argument to emit() is the event name.
 * Any additional arguments are passed on to the event listener.
 */
emit('response', 'hello from child', 'all is well');
</script>

<template>
  <h2>Child component</h2>
</template>
