<template>
  <div>
    <Header />
    <h1>Hello User, Welcome on Update Page</h1>
    <form action="" @submit.prevent="update" class="add">
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
      <button @click="update" type="button">Update New Restaurant</button>
    </form>
  </div>
</template>
<script>
import Header from "./Header.vue";
import axios from "axios";
export default {
  name: "Update",
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
    async update() {
      const results = await axios.put(
        `https://jserver-restaurant.herokuapp.com/restaurants/${this.$route.params.id}`,
        {
          name: this.restaurants.name,
          address: this.restaurants.address,
          contact: this.restaurants.contact,
        }
      );

      if (results.status == 200) {
        this.$router.push({ name: "Home" });
      }
    },
  },
  async mounted() {
    let users = localStorage.getItem("user-info");
    if (!users) {
      this.$router.push({ name: "SignUp" });
    }

    const results = await axios.get(
      `https://jserver-restaurant.herokuapp.com/restaurants/${this.$route.params.id}`
    );

    this.restaurants = results.data;
  },
};
</script>
<style lang=""></style>
