<template>
  <div>
    <form @submit.prevent="addTodo">
      <!--v-model helps with data bindings on form input. It will take the init value from data title-->
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add Todo ..."
        pattern="[A-Za-z0-9]+"
        required
      />
      <input type="submit" value="submit" class="btn" />
    </form>
  </div>
</template>

<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    };
  },
  methods: {
    addTodo() {
      // 1. construct new Todo
      const newTodo = {
        title: this.title,
        completed: false
      };
      // 2. send up to the parent
      this.$emit('add-todo', newTodo);
      //3. clear input after todo is submitted
      this.title = '';
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}

input[type='text'] {
  -ms-flex: 10; /* IE 10 */
  flex: 10;
  padding: 5px;
  outline: none;
}

input[type='submit'] {
  -ms-flex: 2; /* IE 10 */
  flex: 2;
  outline: none;
}
</style>
