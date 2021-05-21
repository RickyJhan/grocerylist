<template>
  <b-row id="app">
    <AddItem v-on:add-todo="addTodo" />
    <GroceryList v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    <p class="total">{{ totalItem }}</p>
    <!-- <input type="number" v-model.number="totalItem(item)" readonly>  -->
  </b-row>
</template>

<script>
import GroceryList from '../components/GroceryList';
import AddItem from '../components/AddItem';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    GroceryList,
    AddItem
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
    },
    totalItem: function (item) {
      return item.price * item.quantity;
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  }
}
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
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>