<template>
  <div id="app">
    <Navbar @search="search"></Navbar>

    <div class="container mt-3">
      <div class="row">
        <Inventory :items="items" @newItemAdded="addToItem"></Inventory>
        <Cart :items="cart" @removeItem="removeToItem"></Cart>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import Cart from "./components/Cart";
import Inventory from "./components/Inventory";
import data from "./data.js";
export default {
  components: {
    Navbar,
    Cart,
    Inventory,
  },
  data(){
    return{
      items:[],
      cart:[]
    }
  },
  mounted(){
    this.items=data
  },
  methods:{
    addToItem(item){
      this.cart.push(item)
    },
    removeToItem(index){
      this.cart.splice(index, 1)
    },
    search(keyword){
      this.items=data.filter(item=>{
       return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !== -1
      })
    }
    
  }
};
</script>

<style>
</style>
