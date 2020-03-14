<template>
  <div>
    <!--add v-for directive to loop over the array of todos -->
    <div v-for="todo in todos" :key="todo.id">
      <!--add v-on to listen for del-todo event, inside we put the some logic that will execute when event happend -->
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<!--add a component name to export -->
<script>
import TodoItem from "./TodoItem";

export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos"]
};
</script>

<style scoped>
</style>