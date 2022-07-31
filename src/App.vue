<script setup lang="ts">
import { onMounted, ref, type Ref } from 'vue';

const paragraph: Ref = ref(null);

 onMounted(() => {
  // component is now mounted.
  paragraph.value.textContent = "text on mount";
});
</script>

<template>
  <p ref="paragraph">hello</p>
</template>
