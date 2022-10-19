<template>
  <div>
    <Header />
    <h1>Hello User, Welcome Homepage</h1>
  </div>
</template>
<script>
import axios from "axios";
import Header from "./Header.vue";
export default {
  name: "Home",
  components: {
    Header,
  },

  async mounted() {
    let users = localStorage.getItem("user-info");
    if (!users) {
      this.$router.push({ name: "SignUp" });
    }

    let results = await axios.get("http://localhost:3000/restaurants");
    console.warn(results);
  },
};
</script>
<style>
body {
  min-height: 0;
}
</style>
