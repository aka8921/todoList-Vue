<template>
    <div class="todos-container">

        <TodoItem :todo="todo" v-for="todo in todos" :key="todo.id"
        v-on:delete-todo="$emit('delete-todo', todo.id)"
        />

    </div>
</template>

<script>
import TodoItem from './TodoItem'
export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script>

<style scoped>
.todos-container{
    padding: 30px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: stretch;
}
</style>