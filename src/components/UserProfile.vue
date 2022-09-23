<script setup>
import { ref } from "vue";

const showMenu = ref(false);

const emit = defineEmits(["loggedOut"]);

const props = defineProps({ username: String });

function logOut() {
  let logOut = false;
  emit("loggedOut", logOut);
}

let borderSize = ref("0.5em");
</script>

<template>
  <div class="container">
    <div
      class="Profile"
      @click="showMenu = !showMenu"
      v-bind:style="[
        showMenu
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
      <b>{{ props.username }}</b>
    </div>
    <ul v-if="showMenu" class="list">
      <li @click="logOut"><b>Log out</b></li>
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
  font-size: 1.2em;
  padding: 0.5em;
  background-color: #0e0e10;
  color: white;
  text-align: center;
  cursor: pointer;
}

.list {
  padding: 0;
  margin-top: 2.4em;
  position: absolute;
  padding: 1em;

  background-color: #50c878;
  border-radius: 0.5em 0.5em 0.5em 0.5em;
}
.list li {
  cursor: pointer;
  text-align: center;
  padding: 1em 1em 1em 1em;
  list-style: none;
  max-width: 100%;
}

.list li:hover {
  background-color: #3d9c5d;
  border-radius: 0.5em 0.5em 0.5em 0.5em;
}
</style>
