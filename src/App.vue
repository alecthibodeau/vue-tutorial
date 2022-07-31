<script setup lang="ts">
import { ref } from 'vue';
import ChildComp from './components/ChildComp.vue';

const message = ref('from parent');
</script>

<template>
  <ChildComp>
    Message: {{ message }}
  </ChildComp>
</template>
