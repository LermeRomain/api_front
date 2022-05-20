<template>
  <div class="container">
    <ul>
      <li v-for="profile in profiles" v-bind:key="profile"> {{ profile.name }} {{profile.surname}}</li>
    </ul>
    <ul>
      <li v-for="company in companys" v-bind:key="company"> {{ company.name }} {{company.url}}</li>
    </ul>


  </div>


</template>

<script>
import axios from "axios";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'ProfileAndCompany',
  data() {
    return {
      profiles: null,
      companys: null
    }
  },
  mounted() {
    axios
        .get('http://89.88.140.151:8840/api/profile/')
        .then(response => (this.profiles = response.data))
    console.log(this.profiles);
    axios
        .get('http://89.88.140.151:8840/api/company/')
        .then(response => (this.companys = response.data))
    console.log(this.companys);
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
