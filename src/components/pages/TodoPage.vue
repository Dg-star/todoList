<template>
    <div class="todo-list">
      <TodoInput @create-new-item="handleItemAdd" />
      <TodoItem v-for="(todoTitle, index) in todoes" :key="index" :todo-title="todoTitle" />
    </div>
</template>

<script setup>
import { ref } from 'vue'
import TodoItem from '../TodoItem.vue'
import TodoInput from '../TodoInput.vue'

const todoes = ref([])

function handleItemAdd(todoTitle) {
    todoes.value.push(todoTitle)
} 
</script>

<style scoped>
.todo-list {
    display: flex;
    flex-direction: column;
    max-width: 450px;
}
</style>