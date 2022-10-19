<template>
  <div>
    <Header />
    <h1>Hello User, Welcome on Add Page</h1>
  </div>
</template>
<script>
import Header from "./Header.vue";
export default {
  name: "Add",
  components: {
    Header,
  },
};
</script>
<style>
body {
  min-height: 0;
}
</style>
