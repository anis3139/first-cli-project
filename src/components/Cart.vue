<template>
  <div class="col-md-3">
    <div class="cart px-3">
      <ul class="list-group">
        <li class="list-group-item">
          <span class="item-name float-left">Title</span>
          <span class="item-name float-right">Price</span>
        </li>
        <li class="list-group-item" v-for="(item, index) in items" :key="index">
          <span class="item-name float-left">{{item.title}}</span>
          <span class="item-name float-right">{{item.price}}</span>
          <span class="btn btn-danger mx-2" @click="remove(index)">-</span>
        </li>
        <li class="list-group-item">
          <span class="item-name float-left">Total</span>
          <span class="item-name float-right">{{totalPrice}}</span>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
 props:['items'],
 computed:{
   totalPrice(){
     var total=0
     this.items.forEach(item => {
       total += parseFloat(item.price.substring(1))
     })
      return total.toFixed(2)
   }
 },
 methods:{
   remove(index){
     this.$emit('removeItem', index)
   }
 }
};
</script>
<style lang="stylus" scoped></style>