<template>
  <div>
    <form>
      <input type="text" name="title" placeholder="Add Todo ..." />
      <input type="submit" value="submit" class="btn" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo"
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  -ms-flex: 10; /* IE 10 */
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  -ms-flex: 2; /* IE 10 */
  flex: 2;
}
</style>