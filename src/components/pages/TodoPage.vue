<template>
    <Header/>

    <div class="todo-list">
      <TodoInput @create-new-item="handleItemAdd" />
      <TodoItem
        v-for="(todoItem, index) in todoes"
                :key="index"
                :todo-item="todoItem"
                @delete-todo-item="handleTodoItemDelete"
        />
    </div>

    <div>
        <h2>Удалённые todoItem</h2>
        <TodoItem
            v-for="(todoItem, index) in deleteTodoes"
            :key="index"
            :is-deleted-todo-item="true"
            :todo-item="todoItem"
            @restore-todo-item="handleTodoItemRestore"
        />
    </div>

    <Footer/>
</template>

<script setup>
import { ref } from 'vue'
import TodoItem from '../TodoItem.vue'
import TodoInput from '../TodoInput.vue'
import Footer from '../TodoFooter.vue'
import Header from '../TodoHeader.vue'

const todoes = ref([])
const deleteTodoes = ref([])

function handleItemAdd(todoTitle) {
    todoes.value.push({
        id: todoes.value.length + deleteTodoes.value.length + 1,
        title: todoTitle,
    })
} 


function handleTodoItemDelete(id) {
    const index = todoes.value.findIndex((todoItem) => todoItem.id === id)

    if ( index !== -1) {
        const deletedItem = todoes.value.splice(index, 1)

        deleteTodoes.value.push(deletedItem[0])
    }
}

function handleTodoItemRestore(id) {
    const index = deleteTodoes.value.findIndex((todoItem) => todoItem.id === id)

    if ( index !== -1) {
        const deletedItem = deleteTodoes.value.splice(index, 1)

        todoes.value.push(deletedItem[0])
    }
}
</script>

<style scoped>
.todo-list {
    display: flex;
    flex-direction: column;
    max-width: 450px;
    margin-right: 100px;
}
</style>