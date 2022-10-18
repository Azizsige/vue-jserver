<template>
  <div>
    <img class="logo" src="./../assets/vue.svg" alt="" srcset="" />
    <h1>Sign Up</h1>
    <div class="login">
      <input v-model="email" type="email" placeholder="Enter Email" />
      <input v-model="password" type="password" placeholder="Enter Password" />
      <button type="submit">Login</button>
    </div>
  </div>
</template>
<script>
export default {};
</script>
<style lang=""></style>
