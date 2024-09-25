<template>
    <div class="shopping-cart">
      <h2>Shopping Cart</h2>
      <div v-if="cart.length > 0">
        <ul>
          <li v-for="(item, index) in cart" :key="index">
            {{ item.name }} ({{ item.quantity }}x) - {{ item.price * item.quantity }}
            <button @click="removeFromCart(index)">Remove</button>
          </li>
        </ul>
        <p>Total: {{ totalPrice }}$</p>
      </div>
      <p v-else>Your cart is empty</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      cart: {
        type: Array,
        required: true
      }
    },
    computed: {
      totalPrice() {
        return this.cart.reduce((sum, item) => sum + item.price * item.quantity, 0);
      }
    },
    methods: {
      removeFromCart(index) {
        this.$emit('remove-from-cart', index);
      }
    }
  }
  </script>
  
  <style>
  .shopping-cart {
    border: 1px solid #ddd;
    padding: 10px;
  }
  button {
    margin-left: 10px;
  }
  </style>
  