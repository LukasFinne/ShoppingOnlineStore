<script setup>
import { ref } from "vue";

const data = ref(null);
const error = ref(null);
const url = "data/db.json";

fetch(url)
  .then((res) => res.json())
  .then((json) => (data.value = json))
  .catch((err) => (error.value = err));
</script>

<template>
  <div class="productContainer">
    <div v-if="error">Error: {{ error }}</div>
    <div
      class="itemContainer"
      v-else-if="data"
      v-for="product in data.products"
      :key="product.id"
    >
      <h3 class="productName">{{ product.name }}</h3>
      <p class="productPrice">{{ product.price }} kr</p>
      <button>Add</button>
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<style scoped>
.productContainer {
  display: flex;
  flex-direction: row;
}
.itemContainer {
  margin: 1em;
  height: 10em;
  width: 10em;
  display: flex;
  flex-direction: column;
  border: solid 1px;
  align-items: center;
}
</style>
