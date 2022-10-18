<template>
  <div>
    <h1>Hello User, Welcome Homepage</h1>
  </div>
</template>
<script>
export default {
  name: "Home",
  mounted() {
    let users = localStorage.getItem("user-info");
    if (!users) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>
<style></style>
