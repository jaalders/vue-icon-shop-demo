<template>
  <div class="col d-flex align-items-stretch">
    <div class="card">
      <font-awesome-icon v-bind:icon="product.icon" class="fa-5x text-center pt-4" />
      <br>
      <div class="card-body">
        <h5 class="card-title">{{ product.name }}</h5>
        <p class="card-text">{{ product.description }}<br></p>
        <div class="position-relative start-1">
          <p>Price: ${{ product.price }}</p>
          <input type="number" v-model="product.quantity">
          <br>
          <br>
          <button @click="addToCart(product.name, product.quantity)">Add to cart</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['product', 'index', 'addToCart'],
    data() {
      return {
        quantity: 0
      }
    }
  }
</script>