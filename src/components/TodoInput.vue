<template>
    <div class="todo-input">
        <input v-model="todoTitle" />
        <button @click="handleAddItem"> Добавить предмет</button>
    </div>
    </template>
    
    <script setup>
    import { ref, defineEmits } from 'vue'
    
    const emit = defineEmits(['create-new-item'])
    
    const todoTitle = ref('')
    
    function handleAddItem() {
        if ( !todoTitle.value) return
    
        emit('create-new-item', todoTitle.value)
    
        todoTitle.value=''
    }
    </script>
    
    <style scoped>
    .todo-input{
        display: flex;
    
        button {
            margin-left: 8px;
        }
    }
    </style>