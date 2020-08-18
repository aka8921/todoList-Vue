<template>
  <div id="app">
    <Header />
    <Todos :todos="todos" class="todos" v-on:delete-todo="deleteTodo"/>
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template> 

<script>
import Header from './components/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
  },
  methods: {
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo]
    },
    deleteTodo(todoId){
      this.todos = this.todos.filter( todo => todo.id != todoId)
    }
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "hello",
          completed: false
        },
        {
          id: 2,
          title: "hello 2",
          completed: true
        }
      ]
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;500;700;900&display=swap');
*{
    padding: 0;
    margin: 0;
    font-family: 'Roboto', sans-serif;
  }
#app{
  background-color: rgb(41, 41, 41);
  color: White;
  min-height: 100vh;
  overflow-x: hidden;

  display: flex;
  flex-direction: column;
}

.todos{
  flex: 1;
}
</style>
