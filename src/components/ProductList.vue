<template>
    <div class="product-list">
      <ProductCard v-for="product in products" :key="product.id" :product="product" @add-to-cart="addToCart" />
    </div>
  </template>
  
  <script>
  import ProductCard from './ProductCard.vue';
  
  export default {
    components: {
      ProductCard
    },
    data() {
      return {
        products: [
          { id: 1, name: 'Chips', price: 10, image: 'https://static.office-discount.de/img/13/26/Zoom_m2298887.jpg?width=800&height=800&fit=contain&bg=ffffff' },
          { id: 2, name: 'Juice', price: 20, image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTigOyzXrl640zG-0K0UzhhmHPl6Nf7q3W11w&s' },
          { id: 3, name: 'Chocolate Cake', price: 30, image: 'https://theloopywhisk.com/wp-content/uploads/2021/04/Small-Batch-Gluten-Free-Birthday-Cake_730px-featured.jpg' },
        ]
      }
    },
    methods: {
      addToCart(product) {
        this.$emit('add-to-cart', product);
      }
    }
  }
  </script>
  
  <style>
  .product-list {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
  </style>
  