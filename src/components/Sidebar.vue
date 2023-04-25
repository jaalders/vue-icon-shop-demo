<script>
  export default {
    props: ["cart", "inventory", "removeitem"],
    methods: {
      getPrice(name) {
        const product = this.inventory.find((p) => {
          return p.name === name
        })
        return product.price
      },
      calculateCartTotal() {
        const total = Object.entries(this.cart).reduce((acc, curr, index) => {
          return acc + (curr[1] * this.getPrice(curr[0]))
        }, 0)
        return total.toFixed(2)
      }
    }
  }
</script>

<template>
  <aside class="cart-container">
        <div class="cart">
          <div class="offcanvas offcanvas-end w-25" tabindex="-1" id="offcanvas" data-bs-keyboard="false" data-bs-backdrop="true">
            <div class="offcanvas-header">
                <h6 class="offcanvas-title d-none d-sm-block" id="offcanvas">Your current shopping cart.</h6>
                <button type="button" class="btn-close text-reset" data-bs-dismiss="offcanvas" aria-label="Close"></button>
            </div>
            <div class="offcanvas-body px-0">
              <ul class="nav nav-pills flex-column mb-sm-auto mb-0 align-items-start" id="menu">
                <!-- you were going from an (item, i) here -->
                <li v-for="(quantity, key, i) in cart" :key="i" class="list-group-item d-flex justify-content-between lh-sm">
                  <div>
                    <h6 class="my-0">{{ key }}</h6>
                    <span class="text-muted">Quantity: {{ quantity }} </span>
                    <br class="clearfix py-4">
                    <span class="text-muted">Sub-total: {{ quantity * getPrice(key) }} </span>
                    <br class="clearfix">
                    <br class="clearfix">
                    <button type="button" @click="removeitem(key)" class="btn btn-light float-right">Remove</button>
                  </div>
                </li>
              </ul>
            </div>
            <div class="spread">
              <span><strong>Total:</strong> ${{ calculateCartTotal() }}</span>
              <button class="btn btn-light">Checkout</button>
            </div>
            <br>
          </div>
        </div>
      </aside>
</template>