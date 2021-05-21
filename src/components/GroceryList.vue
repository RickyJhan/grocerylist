<template>
  <div class="clearfix">
    <div class="row justify-content-between " v-bind:key="todo.id" v-for="todo in todos">
      <GroceryItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
    
  </div>
</template>

<script>
import GroceryItem from './GroceryItem.vue';
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  name: "GroceryList",
  components: {
    GroceryItem
  },
  computed : {
    totalItem: function(){
      let sum = 0;
      for(let i = 0; i < this.items.length; i++){
        sum += (parseFloat(this.items[i].price) * parseFloat(this.items[i].quantity));
      }

     return sum;
   }
  },
  props: ["todos"]
  
}
</script>

<style scoped>

</style>

