<template>
  <div class="about container">
    <h1>Products</h1>
    <div class="row">
      <products-data
      v-for="product in products"
      :key="product.id"
      :product="product"
       />
    </div>
    <div id="nav" >
      <router-link :to="`/addProduct`">Add Product</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
import ProductsData from '../components/ProductsData'
import { mapState } from 'vuex'

export default {
  name: 'Products',
  components: {
    ProductsData
  },
  methods: {
    getProducts () {
      this.$store.dispatch('getProducts')
    }
  },
  created () {
    this.$store.dispatch('getProducts')
  },
  computed: {
    ...mapState([
      'products'
    ])
  }
}
</script>
