<template>
  <ul class="list-group">
    <li v-for="(item, index) in items" :key="index" class="list-group-item">
        <span class="item-name">{{item.title}} : </span>
        <button class="btn btn-sm btn-danger" @click="removeItem(index)">-</button>
        <span class="item-price float-right">{{item.price}}</span>
    </li>
    <hr>
    <li class="list-group-item">
        <span class="item-name"></span>
        <span class="item-price float-right">Total Price : ${{totalPrice}}</span>
    </li>
  </ul>
</template>

<script>
export default {
 props: ['items'],
 computed: {
     totalPrice () {
         var total = 0
         this.items.forEach(item => {
             console.log(item.price)
             total += parseFloat(item.price)
         })
         return total;
     }
 },
 methods: {
     removeItem(index){
        this.$emit('removeItem',index)
     }
 }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
