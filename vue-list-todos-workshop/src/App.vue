<template>
  <div id="app">
    <h1>Listado de tareas</h1>
    <CreatorTodos
      @add-todo="addTodo"/>

      <Filters @change-filter="changeFilter"/>

      <div> Filtro seleccionado: {{ filter }} </div>

      <ListTodos 
        :list-todos="filterTodos"
        @update-todo="updateTodo"/>

      <div>
        <div>Total tareas: {{ todos.length }}</div>
        <div>Total incompletas: {{ todosIncompleted.length }} </div>
        <div>Total completadas: {{ todosCompleted.length }}</div>
      </div>
  </div>
</template>

<script>
import CreatorTodos from './components/CreatorTodos'
import Filters from './components/Filters'
import ListTodos from './components/ListTodos'

export default {
  name: 'App',
  components: {
    CreatorTodos,
    Filters,
    ListTodos
  },
  data() {
    return {
      todos: [
      
      ],
      filter: 'all'
    }
  },
  computed: {
    todosIncompleted() {
      return this.todos.filter(todo => !todo.completed)
    },
    todosCompleted() {
      return this.todos.filter(todo => todo.completed)
    },
    filterTodos() {
      if(this.filter === 'incompleted') {
        return this.todosIncompleted
      }
      if(this.filter === 'completed') {
        return this.todosCompleted
      }
      return this.todos
    }

  },
  methods: {
    addTodo(nameTodo){
      const newTodo = {
        id: Date.now(),
        name: nameTodo,
        completed: false
      }
      this.todos.push(newTodo)
    },
    updateTodo(idTodo) {
      const indexTodo = this.todos.findIndex(todo => todo.id === idTodo)
      this.todos[indexTodo].completed = !this.todos[indexTodo].completed
    },
    changeFilter(nameFilter) {
      this.filter = nameFilter
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
