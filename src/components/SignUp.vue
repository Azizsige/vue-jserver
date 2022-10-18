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
      let results = await axios.post("http://localhost:3000/user", {
        email: this.email,
        password: this.password,
        name: this.name,
      });
      console.warn(results);
      if ((results.status = 201)) {
        alert("signup");
        localStorage.setItem("user-info", JSON.stringify(results.data));
      }
    },
  },
};
</script>
<style>
.logo {
  width: 100px;
}

.register input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin: 0 auto 30px auto;
  border: 1px solid skyblue;
}

.register button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  background-color: skyblue;
  color: #fff;
  cursor: pointer;
}
</style>
