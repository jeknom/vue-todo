<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import TitleComponent from './components/TitleComponent.vue'
import TextInput from './components/TextInput.vue';
import Button from './components/Button.vue';
import { ref } from 'vue';
import generateRandomId from './utils/generateRandomId';

export interface Todo {
  message: string;
  id: string;
}

const newTodo = ref('');
const todos = ref<Todo[]>([]);

function handleNewTodoChange(event: Event) {
  const target = event.target as HTMLInputElement;
  newTodo.value = target.value;
}

function handleNewTodoCreate() {
  todos.value = [...todos.value, { id: generateRandomId(10), message: newTodo.value }];
  newTodo.value = "";
}

function handleDeleteTodo(id: string) {
  todos.value = todos.value.filter(t => t.id !== id);
  console.log(`${id} deleted`);
}
</script>

<template>
  <TitleComponent>Todo app</TitleComponent>
  <div class="horizontal">
    <TextInput
      placeholder="Todo"
      :value="newTodo"
      :onChange="handleNewTodoChange"
    />
    <Button @click="handleNewTodoCreate">Create</Button>
  </div>
  <li v-for="todo in todos">
    <div class="horizontal">
      {{ todo.message }}
      <Button @click="handleDeleteTodo(todo.id)">Delete</Button>
    </div>
  </li>
</template>

<style scoped>
  .horizontal {
    display: flex;
    flex-direction: row;
    gap: 8px;
  }
</style>
