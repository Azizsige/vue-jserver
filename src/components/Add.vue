<template>
  <div>
    <Header />
    <h1>Hello User, Welcome on Add Page</h1>
    <form action="" @submit.prevent="add" class="add">
      <input
        type="text"
        name="name"
        placeholder="Enter Name"
        v-model="restaurants.name"
      />
      <input
        type="text"
        name="address"
        placeholder="Enter Address"
        v-model="restaurants.address"
      />
      <input
        type="text"
        name="contact"
        placeholder="Enter Contact"
        v-model="restaurants.contact"
      />
      <button @click="add" type="button">Add New Restaurant</button>
    </form>
  </div>
</template>
<script>
import Header from "./Header.vue";
import axios from "axios";
export default {
  name: "Add",
  components: {
    Header,
  },
  data() {
    return {
      restaurants: {
        name: "",
        address: "",
        contact: "",
      },
    };
  },
  methods: {
    async add() {
      const results = await axios.post(
        "https://jserver-restaurant.vercel.app/restaurants/",
        {
          name: this.restaurants.name,
          address: this.restaurants.address,
          contact: this.restaurants.contact,
        }
      );
      if (results.status == 201) {
        this.$router.push({ name: "Home" });
      }
    },
  },
  mounted() {
    let users = localStorage.getItem("user-info");
    if (!users) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>
<style>
body {
  min-height: 0;
}
</style>
