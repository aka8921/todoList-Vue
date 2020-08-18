<template>
    <div class="todo" v-bind:class="{'completed':todo.completed}">
        <div class="complete-btn" @click="completeTodo"></div>
        <div class="todo-title">
            {{todo.title}}
        </div>
        <div class="delete-btn" @click="$emit('delete-todo', todo.id)"> X </div>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props:["todo"],
    methods: {
        completeTodo() {
            this.todo.completed = !this.todo.completed
        }
    },
}
</script>

<style scoped>
.todo-title {
  flex-grow: 1;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.todo {
  margin: 0.5rem;
  padding: 10px;
  background-color: rgb(71, 71, 71);
  color: white;
  font-weight: 100;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  width: 80vw;
  border-radius: 0.3em;
  cursor: pointer;
  transition: all 0.3s ease;

  text-overflow: ellipsis;
}

.todo:hover {
  background-color: rgb(88, 88, 88);
}

.complete-btn {
  background-color: rgb(68, 0, 255);
  border-color: black;
  border-width: 10px;
  color: white;
  border: none;
  padding: 0.3rem;
  margin: 1rem;
  cursor: pointer;
  font-size: 1rem;
}

.completed {
  text-decoration: line-through;
  opacity: 0.5;
}

.delete-btn{
    margin-left: auto;
    background-color: red;
    font-weight: 800;
    color: white;
    height: 20px;
    width: 20px;
    border-radius: 20px;
    font-size: 8px;

    display: flex;
    justify-content: center;
    align-items: center;
}
</style>