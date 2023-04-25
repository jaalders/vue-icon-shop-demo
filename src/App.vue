<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Sidebar from "@/components/Sidebar.vue"
import inventory from './icons.json'
</script>

<script>
export default {
  components: {
    Sidebar
  },
  data () {
    return {
      inventory: inventory,
      cart: {},
      activeIndex: 1
    }
  },
  computed: {
    totalQuantity() {
      return Object.values(this.cart).reduce((totalNumberInCart, numberOfItemsAdded) => {
        return totalNumberInCart + numberOfItemsAdded
      }, 0)
    }
  },
  methods: {
    addToCart(productName, quantity) {
      if (!this.cart[productName]) this.cart[productName] = 0
      // pass the 'type' of product from inventory to current user cart.
      this.cart[productName] += quantity
    },
    removeCartItem(name) {
      delete this.cart[name]
    }
  }
}
</script>

<template>
  <div class="container-fluid">
    <header class="d-flex flex-wrap justify-content-center py-3 mb-1">
      <a href="/" class="d-flex align-items-center mb-3 mb-md-0 me-md-auto link-body-emphasis text-decoration-none">
        <font-awesome-icon icon="fas fa-dice-d20" />&nbsp;
        <span class="fs-4 ms-1">IconiCoaster</span>
      </a>
      <ul class="nav nav-pills">
        <li class="nav-item"><RouterLink to="/" @click="activeIndex=1" :class="[activeIndex === 1 ? 'active nav-link' : 'nav-link']">Home</RouterLink></li>
        <li class="nav-item"><RouterLink to="/products" @click="activeIndex=2" :class="[activeIndex === 2 ? 'active nav-link' : 'nav-link']">Products</RouterLink></li>
        <li class="nav-item"><RouterLink to="/past-orders" @click="activeIndex=3" :class="[activeIndex === 3 ? 'active nav-link' : 'nav-link']" >Previous Orders</RouterLink></li>
        <li class="nav-item">        
          <a class="nav-link" data-bs-toggle="offcanvas" data-bs-target="#offcanvas" role="button">
            <font-awesome-icon icon="fas fa-cart-arrow-down" />&nbsp;Cart ({{ totalQuantity }})
          </a>
        </li>
      </ul>
      </header>
    </div>
  <RouterView :inventory="inventory" :addToCart="addToCart"/>
  <Sidebar
    :cart="cart"
    :inventory="inventory"
    :removeitem="removeCartItem"
  />
</template>

