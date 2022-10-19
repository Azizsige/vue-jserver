<template>
  <div>
    <Header />
    <h1>Hello User, Welcome Homepage</h1>
  </div>
</template>
<script>
import Header from "./Header.vue";
export default {
  name: "Home",
  components: {
    Header,
  },
  mounted() {
    let users = localStorage.getItem("user-info");
    if (!users) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>
<style></style>
