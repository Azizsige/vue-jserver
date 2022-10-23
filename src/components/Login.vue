<template>
  <div class="login-wrapper">
    <img class="logo" src="./../assets/vue.svg" alt="" srcset="" />
    <h1>Login</h1>
    <div class="login">
      <input v-model="email" type="email" placeholder="Enter Email" />
      <input v-model="password" type="password" placeholder="Enter Password" />
      <button @click="login" type="submit">Login</button>
    </div>
    <p>
      <router-link to="/sign-up">SignUp</router-link>
    </p>
  </div>
</template>
<script>
import axios from "axios";

export default {
  name: "Login",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async login() {
      let results = await axios.get(
        `http://localhost:3000/user?email=${this.email}&password=${this.password}`
      );
      if ((results.status = 200 && results.data.length > 0)) {
        localStorage.setItem("user-info", JSON.stringify(results.data));
        this.$router.push({ name: "Home" });
      } else {
        alert("Invalid Login");
      }
    },
  },
  mounted() {
    let users = localStorage.getItem("user-info");
    if (users) {
      this.$router.push({ name: "Home" });
    }
  },
};
</script>
<style>
body {
  min-height: 100vh;
}

.login-wrapper {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
