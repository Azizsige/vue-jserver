<template>
  <div class="container-list">
    <ul class="list">
      <li><a href="">Home</a></li>
      <li><a href="">Add Restaurant</a></li>
      <li><a href="">Update Restaurant</a></li>
      <li><a href="">Logout</a></li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "Header",
};
</script>
<style>
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
