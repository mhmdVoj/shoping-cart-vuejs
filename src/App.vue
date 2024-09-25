<template>
  <div id="app">
    <h1>Simple Shopping Cart</h1>
    <ProductList @add-to-cart="addToCart" />
    <ShoppingCart :cart="cart" @remove-from-cart="removeFromCart" />
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';
import ShoppingCart from './components/ShoppingCart.vue';

export default {
  data() {
    return {
      cart: []
    }
  },
  components: {
    ProductList,
    ShoppingCart
  },
  methods: {
    addToCart(product) {
      const cartItem = this.cart.find(item => item.id === product.id);
      if (cartItem) {
        cartItem.quantity++;
      } else {
        this.cart.push({ ...product, quantity: 1 });
      }
    },
    removeFromCart(index) {
      this.cart.splice(index, 1);
    }
  }
}
</script>

<style>
#app {
  max-width: 1200px;
  margin: 0 auto;
}
</style>
