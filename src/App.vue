<script setup lang="ts">
import { ref, type Ref } from 'vue';

interface Todo {
  id: number;
  text: string;
}

// give each todo a unique id
let id = 0;

// provide corresponding ref for template
let itemsNumber: Ref<number | null> = ref(null);

const newTodo = ref('');

const todos = ref([
  { id: id += 1, text: 'Learn HTML' },
  { id: id += 1, text: 'Learn JavaScript' },
  { id: id += 1, text: 'Learn Vue' }
]);

function addTodo() {
  todos.value.push({ id: id += 1, text: newTodo.value });
  newTodo.value = '';
  itemsNumber.value = id;
}

function removeTodo(todo: Todo) {
  todos.value = todos.value.filter((todoToRemove) => todoToRemove !== todo);
  id -= 1;
  if (itemsNumber.value) itemsNumber.value -= 1;
}
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo">
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <div>
    {{ `Current number of list items: ${itemsNumber ? itemsNumber : todos.length}` }}
  </div>
</template>
