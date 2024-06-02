<template>
    <ul v-if="todos.length > 0">
        <li v-for="todo in todos" :key="todo.id" class="flex gap-3 mt-2">
            <br />
            <button class="w-5 text-white bg-red-500" @click="deleteTodo(todo.id)">X</button>
            <button class="w-5 text-white bg-green-500" @click="completeTodo(todo.id)">V</button>
            <p :class="{'line-through' : todo.complete}">{{ todo.text }}</p>
        </li>
    </ul>

    <p v-else>No todos found.</p>
</template>

<script setup>

import { defineProps, defineEmits } from "vue";

defineProps({
    todos: {
        type: Array
    }
})

const emit = defineEmits(["deletTodo", "completeTodo"])

const deleteTodo = (todoId) => {
    emit('deletTodo', todoId);
};

const completeTodo = (todoId) => {
    emit('completeTodo', todoId);
};

</script>
