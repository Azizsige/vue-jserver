<template>
  <div>
    <Header />
    <h1>Hello User, Welcome Homepage</h1>

    <div class="table">
      <table border="1">
        <tr>
          <td>No.</td>
          <td>Nama</td>
          <td>Kontak</td>
          <td>Alamat</td>
          <td>Action</td>
        </tr>
        <tr v-for="data in restaurants" :key="data.id">
          <td>{{ data.id }}</td>
          <td>{{ data.name }}</td>
          <td>{{ data.contact }}</td>
          <td>{{ data.address }}</td>
          <td>
            <router-link :to="`/update/${data.id}`">Update</router-link>
            <button type="button" @click="deleteData(data.id)">Delete</button>
          </td>
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

  methods: {
    async deleteData(id) {
      const results = await axios.delete(
        `http://localhost:3000/restaurants/${id}`
      );
      console.log(results);
      if (results.status == 200) {
        this.loadData();
      }
    },

    async loadData() {
      let users = localStorage.getItem("user-info");
      if (!users) {
        this.$router.push({ name: "SignUp" });
      }
      let results = await axios.get("http://localhost:3000/restaurants");
      this.restaurants = results.data;
    },
  },

  async mounted() {
    this.loadData();
    // let users = localStorage.getItem("user-info");
    // if (!users) {
    //   this.$router.push({ name: "SignUp" });
    // }
    // let results = await axios.get("http://localhost:3000/restaurants");
    // this.restaurants = results.data;
  },
};
</script>
<style>
body {
  min-height: 0 !important;
}
</style>
