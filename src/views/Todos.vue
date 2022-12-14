<template>
    <div>
      <h2>To do</h2>
      <AddTodo @addTodo="addTodo"></AddTodo>
      <select v-model="filter">
        <option value="all">All</option>
        <option value="completed">Completed</option>
        <option value="not-completed">Not completed</option>
      </select>
      <hr>
      <TodoListVue v-bind:todos="filteredTodos" @remove-todo="removeTodo"></TodoListVue>
    </div>
  </template>

<script>
import TodoListVue from '../components/TodoList.vue';
import AddTodo from '../components/AddTodo.vue'

export default {
  name: 'App',
  data() {
    return {
      todos: [],
      filter: 'all'
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=25')
  .then(response => response.json())
  .then(json => {
    this.todos =  json
  })
  },
  components: {
    TodoListVue,
    AddTodo,
  },
//   watch: {
//     filter(value) {
//         console.log(value)
//     }
//   },
computed: {
    filteredTodos() {
        if(this.filter === "all") {
            return this.todos
        }

        if(this.filter === "completed") {
            return this.todos.filter(todo => todo.completed)
        }

        if(this.filter === "not-completed") {
            return this.todos.filter(todo => !todo.completed)
        }
    }
},
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  }
}
</script>