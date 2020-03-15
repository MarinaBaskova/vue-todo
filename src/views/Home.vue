<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <!--use v-bind directive to pass todos data as props -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },

  data() {
    return {
      todos: []
    };
  },

  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => (this.todos = this.todos.filter(todo => todo.id !== id)))
        .catch(err => console.log(err.message));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed
        })
        .then(res => (this.todos = [...this.todos, res.data]))
        .catch(err => console.log(err.message));
    }
  },
  // special method, fires off when component loads(works simmilar to ComponentDidMount in React)
  created() {
    axios
      .get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => (this.todos = res.data))
      .catch(err => console.log(err.message));
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
  font-size: 62.5%;
}

.btn {
  display: inline-block;
  border: none;
  background: #e3eaa7;
  color: black;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #c1946a;
}
</style>
