<template>
    <form @submit.prevent="onSubmit">
        <div>
            <input class="border-gray-400 border-[2px] rounded-sm p-1 text-lg" type="text" placeholder="Todo List" v-model="text"/>
        </div>
        <div class="mt-2">
            <button class="w-full p-2 text-white bg-blue-500 rounded-sm">加入清單</button>
        </div>
    </form>
</template>

<script setup>
import { ref } from "vue";

const text = ref("");

const emit = defineEmits("addtodo");

const onSubmit = () => {
    const todo = {
        id : crypto.randomUUID(),
        text : text.value,
        complete : false
    }
    emit('addTodo',todo);
}
</script>
