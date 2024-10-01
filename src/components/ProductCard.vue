<template>
    <div class="product-card">
      <img :src="product.image" alt="product image" width="100" 
      height="100"/>
      <h3>{{ product.name }}</h3>
      <p>{{ product.price }}$</p>
      <button @click="addToCart">Add to Cart</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      product: {
        type: Object,
        required: false
      }
    },
    methods: {
      addToCart() {
        this.$emit('add-to-cart', this.product);
      }
    }
  }
  </script>
  
  <style>
  .product-card {
    border: 1px solid #ddd;
    padding: 10px;
    text-align: center;
    margin-bottom: 20px;
  }
  .product-card img {
    max-width: 100%;
    height: auto;
  }
  button {
    margin-top: 10px;
  }
  </style>
  