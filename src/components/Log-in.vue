<script setup>
import { ref } from "vue";

const showMenu = ref(false);

const emit = defineEmits(["loggedIn"]);

function login() {
  let login = true;

  emit("loggedIn", login);
}

let borderSize = ref("0.5em");
</script>

<template>
  <div>
    <div
      id="login"
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
      Login
    </div>

    <form v-if="showMenu" action="#">
      <label for="uname"><b>Username</b></label>
      <input type="text" name="uname" placeholder="Enter Username" required />
      <label for="psw"><b>Password</b></label>
      <input type="password" placeholder="Enter Password" name="psw" required />

      <button type="submit" @click="login">Login</button>
    </form>
  </div>
</template>

<style scoped>
#login {
  padding: 0.5em;
  background-color: #0e0e10;
  color: white;
  text-align: center;
  cursor: pointer;
}

form {
  display: flex;
  position: absolute;
  flex-direction: column;
  padding: 1em;
  background-color: #50c878;
  border-radius: 0em 0.5em 0.5em 0.5em;
}

form button {
  margin-top: 0.5em;
}
</style>
