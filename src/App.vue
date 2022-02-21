<template>
  <NavBar @search="search" />
  <div class="container">
    <div class="row ">
      <div class="col-md-9" >
        <InventoryComponent @newItemAdded="addCartItem"  :items="items" />
      </div>
      <div class="col-sm-3">
        <CartComponent @removeItem="removeItem" :items="cart" />
      </div>
    </div>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import InventoryComponent from './components/InventoryComponent.vue'
import CartComponent from './components/CartComponent.vue'
import data from './data.js'


export default {
  name: 'App',
  components: {
    NavBar,
    InventoryComponent,
    CartComponent
  },
  data() {
    return {
      items: '',
      cart: [
        {
          id: 1,
          title: 'Rice',
          photo: "http://dummyimage.com/250x250.png/cc0000/ffffff",
          price: 0,
        }
      ]
    }
  },
  mounted() {
    this.items = data;
  },
  methods: {
    addCartItem(item){
      this.cart.push(item)
    },
    removeItem(index){
      this.cart.splice(index,1)
    },
    search(keyword){
      this.items = data.filter(item => {
        return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !==  -1
      })
    }

  }
}
</script>

<style>
  .container{
    padding-top: 10px;
  }
</style>
