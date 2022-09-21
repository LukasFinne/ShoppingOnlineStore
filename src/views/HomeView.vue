<script setup>
import { ref } from "vue";
import ProductList from "../components/Product-list.vue";
import CartList from "../components/CartList.vue";

let cart = ref([]);

const handleCart = (product) => {
  cart.value.push(product);
};

const handleList = () => {
  while (cart.value.length > 0) {
    cart.value.pop();
  }
};

const handleRemoveItem = (id) => {
  if (id > -1) {
    cart.value.splice(id, 1);
  }
};
</script>

<template>
  <header>
    <CartList
      :name="cart"
      @checkOut="handleList"
      @removeItem="handleRemoveItem"
    />
  </header>
  <main><ProductList @addToCart="handleCart" /></main>
</template>

<style scoped></style>
