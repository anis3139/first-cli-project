<template>
  <div class="col-md-9 row">
    <div class="item col-md-4" v-for="(item, index) in items" :key="index">
      <div class="card p-3" style="width: 18rem">
        <img
          class="card-img-top"
          :src="item.image"
          alt="Card image cap"
          width="200px" height="250px"
        />
        <div class="card-body">
          <h5 class="card-title">{{item.title}}</h5>
          <p class="card-text">
           {{item.price}}
          </p>
          <a @click="addToCart(item)" class="btn btn-primary">+Add</a>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
   props:["items"],
   methods:{
     addToCart(item){
       this.$emit('newItemAdded', item)
     }
   }
};
</script>
<style lang="stylus" scoped></style>
