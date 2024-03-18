<template>
    <div class="todo-item">
        {{ props.todoTitle }}
    </div>
</template>

<script setup>
import { defineProps } from 'vue'

const props = defineProps({
    todoTitle: {
        type: String,
        required: true,
    }
})
</script>

<style scoped>
.todo-item{
    margin: 8px 0;
    padding: 9px 30px;
    border-radius: 15px;
    background-color: black;
    color: aliceblue;
}
</style>