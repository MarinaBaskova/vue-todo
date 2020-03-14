<template>
  <div>
    <!--add v-for directive to loop over the array of todos -->
    <div v-for="todo in todos" :key="todo.id">
      <TodoItem v-bind:todo="todo" />
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