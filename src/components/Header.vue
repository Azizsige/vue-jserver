<template>
  <div class="container-list">
    <ul class="list">
      <li><router-link to="/">Home</router-link></li>
      <li><router-link to="/add">Add Restaurant</router-link></li>
      <li><a @click="logout" href="">Logout</a></li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "Header",
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "SignUp" });
    },
  },
};
</script>
<style>
body {
  min-height: 0;
}

.container-list {
  background-color: #f1f1f1;
  width: 100%;
  padding: 10px;
}

.list {
  list-style: none;
  display: flex;
  justify-content: space-around;
  padding: 0;
  margin: 0;
}

.list li {
  padding: 10px;
}

.list li a {
  text-decoration: none;
  color: #000;
}

.list li a:hover {
  color: #f00;
}
</style>
