<template>
  <ProfileAndCompany />
  <create />
</template>

<script>

import ProfileAndCompany from "@/components/ProfileAndCompany";
import Create from "@/components/Create";

export default {
  name: 'App',
  components: {
    Create,
    ProfileAndCompany,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
