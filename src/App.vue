<script setup>
import { RouterLink, RouterView } from "vue-router";
import LogIn from "./components/Log-in.vue";
import { ref } from "vue";
import UserProfile from "./components/UserProfile.vue";

let logIn = ref(false);

const handleLogin = (x) => {
  logIn.value = x;
};
</script>

<template>
  <header>
    <h2>ShoppingGreen</h2>
    <nav>
      <RouterLink class="routerLinks" to="/"><b> Home</b></RouterLink>
      <RouterLink class="routerLinks" to="/about"><b>About</b></RouterLink>
      <LogIn v-if="!logIn" @loggedIn="handleLogin" />
      <UserProfile v-else @loggedOut="handleLogin">Profile</UserProfile>
    </nav>
  </header>
  <RouterView />
  <footer>
    <nav>
      <a href="#">Instagram</a>
      <a href="#">Facebook</a>
      <p>Contact us: shopping_green@Us.com</p>
    </nav>
  </footer>
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
  box-shadow: rgba(99, 99, 99, 0.2) 0em 0.125em 0.5em 0em;
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

.routerLinks {
  text-decoration: none;
  color: white;
  padding: 0.5em;
  font-size: 1.2em;
  border-radius: 0.5em;
  background-color: #50c878;
  box-shadow: rgba(99, 99, 99, 0.2) 0em 0.125em 0.5em 0em;
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
