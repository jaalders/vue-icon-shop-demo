<script setup>
import inventory from '../icons.json'
import ProductCard from '@/components/ProductCard.vue'
</script>

<template>
  <div class="container-fluid overflow-hidden hero pb-4">
    <div class="row">
      <div class="col-2"></div>
      <div class="col-8">
        <h2 class="text-center">A full selection of coasters to choose from!</h2>
      </div>
      <div class="col-2"></div>
    </div>
  </div>

  <div class="container-fluid">
    <div class="row row-cols-1 row-cols-md-4 g-4">
      <ProductCard 
          v-for="(product, index) in inventory.slice(0, 8)" 
          :key="product.id"
          :index="index"
          :product="product"
          :addToCart="addToCart"
        />
    </div>
  </div>
</template>

<script>
  export default {
    props: ['inventory', 'addToCart'],
    components: {
      ProductCard
    }
  }
</script>