<template>
  <div class="row">
    <div v-for="(item, index) in items" :key="index" class="col-sm-4">
      <div class="card ml-2" style="width: 13rem;">
        <div class="card-body">
          <img :src="item.photo" alt="">
          <h5 class="card-title">{{item.title}}</h5>
          <p class="card-text">{{item.price}}</p>
          <a @click="addToCart(item)" class="btn btn-primary">+ Add</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['items'],
  methods: {
    addToCart(item) {
        this.$emit('newItemAdded',item)
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
