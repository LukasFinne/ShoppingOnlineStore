<script setup>
import { ref } from "vue";

const data = ref(null);
const error = ref(null);
const url = "data/db.json";

const emit = defineEmits(["addToCart"]);

function add(product) {
  emit("addToCart", product);
}

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
      <h2 class="productName">{{ product.name }}</h2>
      <p class="productPrice">{{ product.price }} kr</p>
      <button class="button" @click="add(product)">Add</button>
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<style scoped>
.productContainer {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
p {
  font-size: 1.5em;
  margin: 0;
  margin-bottom: 0.5em;
}
.itemContainer {
  color: #0e0e10;

  background-color: #50c878;
  margin: 1em;
  height: 10em;
  width: 10em;
  box-shadow: rgba(99, 99, 99, 0.2) 0em 0.125em 0.5em 0em;
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 0.5em;
}
</style>
