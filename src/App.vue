<template>
  <div>
    <router-view></router-view>
  </div>
</template>
<script>
// import SignUp
import SignUp from "./components/SignUp.vue";
import Login from "./components/SignUp.vue";
export default {
  components: {
    SignUp,
    Login,
  },
};
</script>
<style>
.logo {
  width: 100px;
}

.register input,
.login input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin: 0 auto 30px auto;
  border: 1px solid skyblue;
}

.register button,
.login button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  background-color: skyblue;
  color: #fff;
  cursor: pointer;
}
</style>
