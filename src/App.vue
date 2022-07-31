<script setup lang="ts">
import { computed, ref } from 'vue';

interface Todo {
  id: number;
  text: string;
  done: boolean;
}

let id = 0;

const newTodo = ref('');

const hideCompleted = ref(false);

const todos = ref([
  { id: id += 1, text: 'Learn HTML', done: true },
  { id: id += 1, text: 'Learn JavaScript', done: true },
  { id: id += 1, text: 'Learn Vue', done: false }
]);

const filteredTodos = computed(() => {
  // return filtered todos based on
  // `todos.value` & `hideCompleted.value`
  return hideCompleted.value
    ? todos.value.filter((todo) => !todo.done)
    : todos.value
})

function addTodo() {
  todos.value.push({ id: id += 1, text: newTodo.value, done: false });
  newTodo.value = '';
}

function removeTodo(todo: Todo) {
  todos.value = todos.value.filter((todoToRemove) => todoToRemove !== todo);
}
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" />
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>
