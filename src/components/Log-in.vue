<script setup>
import { ref } from "vue";

const showMenu = ref(false);

const emit = defineEmits(["loggedIn", "username"]);

function login() {
  let login = true;
  emit("loggedIn", login);
}

function username() {
  let username = document.querySelector("#username").value;
  emit("username", username);
}

let borderSize = ref("0.5em");
</script>

<template>
  <div class="container">
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
      <b> Login</b>
    </div>
    <div class="test">
      <form v-if="showMenu" action="#">
        <label><b>Username</b></label>
        <input
          id="username"
          type="text"
          name="uname"
          placeholder="Enter"
          required
        />
        <label for="psw"><b>Password</b></label>
        <input
          type="password"
          placeholder="Enter Password"
          name="psw"
          required
        />

        <button
          type="submit"
          @click="
            login();
            username();
          "
        >
          Login
        </button>
      </form>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  align-items: center;
  flex-direction: column;
}

#login {
  padding: 0.5em;
  font-size: 1.2em;
  background-color: #0e0e10;
  color: white;
  text-align: center;
  cursor: pointer;
}
.test {
  margin-top: 2.4em;
  position: absolute;
}
form {
  display: flex;
  flex-direction: column;
  padding: 1em;
  box-shadow: rgba(99, 99, 99, 0.2) 0em 0.125em 0.5em 0em;
  background-color: #50c878;
  border-radius: 0.5em 0.5em 0.5em 0.5em;
}

form button {
  margin-top: 0.5em;
}
</style>
