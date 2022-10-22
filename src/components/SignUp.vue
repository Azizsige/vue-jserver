<template>
  <div>
    <img class="logo" src="./../assets/vue.svg" alt="" srcset="" />
    <h1>Sign Up</h1>
    <div class="register">
      <input v-model="name" type="text" placeholder="Enter Name" />
      <input v-model="email" type="email" placeholder="Enter Email" />
      <input v-model="password" type="password" placeholder="Enter Password" />
      <button @click="signUp" type="submit">Sign Up</button>
    </div>
    <p>
      <router-link to="/login">Login</router-link>
    </p>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "SignUp",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async signUp() {
      let results = await axios.all([
        axios.post("http://localhost:3000/user", {
          email: this.email,
          password: this.password,
          name: this.name,
        }),
        axios.post("https://azizsige.github.io/vue-jserver/db/db.json", {
          email: this.email,
          password: this.password,
          name: this.name,
        }),
      ]);
      console.warn(results);
      if ((results.status = 201)) {
        localStorage.setItem("user-info", JSON.stringify(results.data));
        this.$router.push({ name: "Home" });
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
</style>
