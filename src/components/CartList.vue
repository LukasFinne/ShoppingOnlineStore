<script setup>
import { ref } from "vue";

let showCart = ref(false);

let totalPrice = ref(0);

const emit = defineEmits(["checkOut", "removeItem"]);
const props = defineProps({
  item: Array,
});

function addToPrice() {
  let temp = 0;
  for (let i = 0; i < props.item.length; i++) {
    temp += props.item[i].price;
  }
  if (totalPrice.value != temp) {
    totalPrice.value = temp;
  }
}
function show() {
  return (showCart.value = true);
}
function hide() {
  return (showCart.value = false);
}

function checkOut() {
  emit("checkOut");
}

function removeItem(id) {
  totalPrice.value -= props.item[id].price;
  emit("removeItem", id);
}

let borderSize = ref("0.5em");
</script>

<template>
  <div class="container">
    <div @mouseover="show()" @mouseleave="hide()">
      <div
        class="btnCart"
        @mouseover="
          show();
          addToPrice();
        "
        v-bind:style="[
          showCart
            ? {
                borderTopLeftRadius: borderSize,
                borderTopRightRadius: borderSize,
              }
            : {
                borderTopLeftRadius: borderSize,
                borderTopRightRadius: borderSize,
                borderBottomLeftRadius: borderSize,
                borderBottomRightRadius: borderSize,
              },
        ]"
      >
        <b> Cart</b>({{ props.item.length }})
      </div>
      <ul v-if="showCart" class="cartList">
        <li v-for="(product, index) in props.item" :key="product.id">
          {{ product.name }} {{ product.price }}kr
          <button @click="removeItem(index)">remove</button>
        </li>
        <button @click="checkOut">Check out</button>
        <div>Total:{{ totalPrice }}</div>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  margin: 0.7em 2em 0.5em 0.5em;
}
.btnCart {
  font-size: 1.2em;
  padding: 0.5em;
  background-color: #0e0e10;
  color: white;
  text-align: center;
  cursor: pointer;
}

.cartList {
  padding: 0;
  margin: auto;
  position: absolute;
  padding: 1em;
  box-shadow: rgba(99, 99, 99, 0.2) 0em 0.125em 0.5em 0em;
  background-color: #50c878;
  border-radius: 0em 0.5em 0.5em 0.5em;
}
.cartList li {
  cursor: pointer;
  text-align: center;
  padding: 1em 1em 1em 1em;
  list-style: none;
  max-width: 100%;
}

.cartList li:hover {
  background-color: #3d9c5d;
  border-radius: 0.5em 0.5em 0.5em 0.5em;
}
</style>
