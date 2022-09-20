<script setup>
import { RouterLink, RouterView } from "vue-router";
import LogIn from "./components/Log-in.vue";
import { ref } from "vue";
import UserProfile from "./components/UserProfile.vue";
import ProductList from "./components/Product-list.vue";
import CartList from "./components/CartList.vue";

let logIn = ref(false);
let cart = ref([]);

const handleCart = (product) => {
  cart.value.push(product);
};

const handleLogin = (x) => {
  logIn.value = x;
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
    <h2>ShoppingGreen</h2>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <LogIn v-if="!logIn" @loggedIn="handleLogin" />
      <UserProfile v-else @loggedOut="handleLogin">Profile</UserProfile>
      <CartList
        :name="cart"
        @clearList="handleList"
        @removeItem="handleRemoveItem"
      />
    </nav>
  </header>
  <ProductList @addToCart="handleCart" />
  <footer>
    <nav>
      <a href="#">Instagram</a>
      <a href="#">Facebook</a>
      <p>Contact us: shopping_green@Us.com</p>
    </nav>
  </footer>
  <RouterView />
</template>

<style scoped>
header {
  display: flex;
  padding: 2em;
  max-width: 100%;
  margin: auto;
  justify-content: space-evenly;
  align-items: center;
  border-bottom: 1px solid;
}

header h2 {
  max-width: 15%;
  max-height: 10%;
  padding: 0.5em;
  border-radius: 1em;
  background-color: #50c878;
  color: white;
}

header p {
  margin: 0;
}

header nav {
  display: flex;
  flex-grow: 2;
  max-width: 100%;
  justify-content: space-evenly;
  align-items: baseline;
}

footer nav {
  border-top: 1px solid;
  display: flex;
  justify-content: space-evenly;
  align-items: baseline;
}
</style>

<style>
body {
  background-color: white;
  max-width: 70%;
  margin: auto;
}
</style>
