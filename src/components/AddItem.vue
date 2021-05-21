<template>
  <div  class="clearfix">
    <form @submit.prevent="addTodo">
      <b-form-input type="text" v-model="title" name="title" placeholder="Add Grocery Item..." ></b-form-input>
      <b-form-input type="submit" value="Submit" class="btn"  v-bind:disabled="!title" ></b-form-input>
    </form>
  </div>
</template>

<script>
// import uuid from 'uuid';
export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo() {
      const newTodo = {
        title: this.title,
        completed: false
      }
      this.$emit('add-todo', newTodo);
      this.title = '';
      // Send up to parent
      
    },

  }
}
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="text"] {
    flex: 10;
    padding: 5px;
  }

  input[type="submit"] {
    flex: 2;
  }
  input[type="submit"]:disabled {
    background-color: black;
    opacity: 0.5;
    cursor: not-allowed;
  }
</style>