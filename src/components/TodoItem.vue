<template>
    <div class="todo-item">
        {{ props.todoItem.title }} {{ props.todoItem.id }}

        <button v-if=" !props.isDeletedTodoItem" @click="handleDelete(props.todoItem.id)">
             Удалить 
        </button>
        <button v-if="props.isDeletedTodoItem" @click="handleRestore(props.todoItem.id)">
             Восстановить
        </button>
    </div>
</template>

<script setup>
import { defineEmits, defineProps } from 'vue'

const emit = defineEmits(['delete-todo-item', 'restore-todo-item'])

const props = defineProps({
    todoItem: {
        type: Object,
        required: true,
    },
    isDeletedTodoItem: {
        type: Boolean,
        default: false
    }
})

function handleDelete(id) {
    emit('delete-todo-item', id)
}

function handleRestore(id) {
    emit('restore-todo-item', id)
}
</script>

<style scoped>
.todo-item{
    display: flex;
    justify-content: space-between;
    margin: 8px 0;
    padding: 9px 30px;
    border-radius: 15px;
    background-color: black;
    color: aliceblue;
}
</style>