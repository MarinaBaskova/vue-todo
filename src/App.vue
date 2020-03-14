<template>
  <div id="app">
    <Header />
    <AddTodo />
    <!--use v-bind directive to pass todos data as props -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from "./components/layout/Header";
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";

export default {
  name: "App",
  components: {
    Header,
    Todos,
    AddTodo
  },

  data() {
    return {
      todos: [
        {
          id: 1,
          title: "First todo",
          completed: false
        },
        {
          id: 2,
          title: "Second todo",
          completed: true
        },
        {
          id: 3,
          title: "Third todo",
          completed: false
        }
      ]
    };
  },

  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
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
