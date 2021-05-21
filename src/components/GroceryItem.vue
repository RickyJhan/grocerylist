<template>
  <div class="groceryitem-item col" v-bind:class="{'is-complete':groceryitem.completed}">
      <input type="checkbox" v-on:change="markComplete" v-bind:checked="groceryitem.completed">
      <input type="number" min="0" class="quantity col-2" placeholder="Quantity">
      <input type="text" v-model="todo.title">
      <input type="number" min="0" class="quantity col-2" placeholder="Price">
      <!-- <button class="del" v-on:click="showAlert"  @click="$emit('del-todo', todo.id)" >x</button> -->

      <input type="text" v-model="item.name">
      <input type="number" v-model.number="item.quantity" min="1">
      <input type="number" v-model.number="item.price" min="0.00" max="1000000000.00" step="0.01">
      <!-- <input type="number" v-model.number="totalItem(item)" readonly> -->
      <button v-on:click="remove(index)">X</button>
  </div>
</template>

<script>
export default {
  name: "GroceryItem",
  props: ["groceryitem"],
  methods: {
    markComplete() {
      this.groceryitem.completed = !this.groceryitem.completed;
    },
    showAlert(){
      return alert('are you sure?');
    }
  }
}
</script>

<style scoped>
  .groceryitem-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }

  .is-complete {
    text-decoration: line-through;
  }

  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
    display: block;
    width: 30px;
    height: 30px;
    line-height: 0px;
  }
</style>

