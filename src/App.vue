<script setup>
import { RouterLink, RouterView } from "vue-router";
import LogIn from "./components/Log-in.vue";
</script>

<template>
  <header>
    <h2>ShoppingGreen@Us</h2>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <LogIn />

      <p>Cart</p>
    </nav>
  </header>

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
  max-height: 5%;
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
  max-width: 80%;
  justify-content: space-evenly;
  align-items: baseline;
}

footer nav {
  display: flex;
  justify-content: space-evenly;
  align-items: baseline;
}
</style>

<style>
body {
  background-color: white;
}
</style>
