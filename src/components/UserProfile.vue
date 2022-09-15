<script setup>
import { ref } from "vue";

const showMenu = ref(false);

const emit = defineEmits(["loggedOut"]);

function logOut() {
  let logOut = false;
  emit("loggedOut", logOut);
}
</script>

<template>
  <div class="container">
    <div class="Profile" @click="showMenu = !showMenu">Profile</div>
    <ul v-if="showMenu" class="list">
      <li>Username</li>
      <li @click="logOut">Log out</li>
    </ul>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.Profile {
  cursor: pointer;
}

.list {
  padding: 0;
  margin-top: 1.5em;
  position: absolute;
}
.list li {
  cursor: pointer;
  background-color: red;
  text-align: center;
  padding: 1em 1em 1em 1em;
  list-style: none;
}

.list li:hover {
  background-color: aliceblue;
}
</style>
