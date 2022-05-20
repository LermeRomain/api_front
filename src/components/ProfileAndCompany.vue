<template>
  <div class="container">
    <h6> {{profiles}} </h6>
    <h6> {{company}} </h6>
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
      company: null
    }
  },
  mounted () {
    axios
        .get('http://89.88.140.151:8840/api/profile/')
        .then(response => (this.profiles = response.data))
    console.log(this.profiles);
    axios
        .get('http://89.88.140.151:8840/api/company/')
        .then(response => (this.company = response.data))
    console.log(this.company);
  }
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
