<template>
    <div class="form-container">
        <form @submit.prevent="addTodo">
        <input type="text" class="todo-input" id="input" v-model="todo"/>
        <button class="todo-button" type="submit">
          Add
        </button>
      </form>
    </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
    name: "AddTodo",
    methods: {
        addTodo() {
            const newTodo = {
                id: uuidv4(),
                title: this.todo,
                completed: false
            }

            this.$emit('add-todo', newTodo)
            this.todo = ""

        }
    },
    data() {
        return {
            todo: ''
        }
    },
}
</script>

<style scoped>
.form-container {
  background-color: rgb(59, 59, 59);
  padding: 1em;
}

.todo-input {
    padding: 0 10px;
  height: 50px;
  border: none;
  border-radius: 0.1em;
  background-color: rgb(71, 71, 71);
  color: white;
  flex-grow: 1;
}

.todo-input:focus {
  outline: none;
}

form {
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.todo-button {
  background-color: rgb(68, 0, 255);
  margin: 1em;
  color: #d88771;
  cursor: pointer;
  transition: all 0.1s ease;
  color: White;
  border: none;
  padding: 1em 2em;
  border-radius: 0.5em;
}

form button:hover {
  background-color: rgb(60, 2, 219);
}

@media screen and (max-width: 600px) {
  form {
    flex-direction: column;
    align-items: stretch;
  }
}

</style>

