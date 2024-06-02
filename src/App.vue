<script setup>

import AddTodo from './components/AddTodo.vue';
import Todolist from './components/Todolist.vue';
import { ref } from "vue";

const todos = ref([
  {
    id: 1,
    text: "Vue測試題"
  }
]);

const handleAddTodo = (todo) => {
  todos.value.push(todo)
  console.log("handleAddTodo", todo);
}

const handleDeletTodo = (todoId) => {
  todos.value = todos.value.filter((todo) => todo.id !== todoId)
}

const handleCompleteTodo = (todoId) => {
  todos.value = todos.value.map((todo) => todo.id === todoId ? {...todo,complete : !todo.complete} : todo)
}

</script>

<template>
  <div>
    <AddTodo @add-todo="handleAddTodo" />
    <Todolist :todos="todos" @delet-todo="handleDeletTodo" @complete-todo="handleCompleteTodo"/>
  </div>
</template>
