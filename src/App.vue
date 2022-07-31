<script setup lang="ts">
import { ref } from 'vue';
import ChildComp from './components/ChildComp.vue';

const childMessage = ref('No child message yet');
const secondaryMessage = ref('Nothing to report');
</script>

<template>
  <ChildComp @response="(message, addedMessage) => {
      childMessage = message;
      secondaryMessage = addedMessage;
    }"
  />
  <p>{{ `${childMessage} ${secondaryMessage}` }}</p>
</template>
