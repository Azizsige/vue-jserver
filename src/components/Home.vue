<template>
  <div>
    <Header />
    <h1>Hello User, Welcome Homepage</h1>

    <div class="table">
      <table border="1">
        <tr>
          <td>Nama</td>
          <td>Kontak</td>
          <td>Alamat</td>
        </tr>
        <tr v-for="data in restaurants" :key="id">
          <td>{{ data.name }}</td>
          <td>{{ data.contact }}</td>
          <td>{{ data.address }}</td>
        </tr>
      </table>
    </div>
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
  data() {
    return {
      restaurants: [],
    };
  },

  async mounted() {
    let users = localStorage.getItem("user-info");
    if (!users) {
      this.$router.push({ name: "SignUp" });
    }

    let results = await axios.get("http://localhost:3000/restaurants");
    this.restaurants = results.data;
    console.log(this.restaurants);
  },
};
</script>
<style>
body {
  min-height: 0 !important;
}
</style>
