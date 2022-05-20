<template>
  <div class="container">
    <ul v-for="profile in profiles" v-bind:key="profile">
      <li> {{ profile.name }} {{ profile.surname }}</li>
      <button v-on:click="deleteProfile(profile.id)">Delete</button>
      <button v-on:click="updateProfile(profile.id)">update</button>
      <div class="form-group">
        <label>Name</label>
        <input type="text" class="form-control" v-model="profile.name"><br>
        <label>username</label>
        <input type="text" class="form-control" v-model="profile.username"><br>
        <label>phone</label>
        <input type="text" class="form-control" v-model="profile.phone"><br>
        <label>company</label>
        <input type="text" class="form-control" v-model="profile.company"><br>
      </div>
    </ul>
    <ul>
      <li v-for="company in companys" v-bind:key="company"> {{ company.name }} {{ company.url }}</li>
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

  methods: {
    deleteProfile(id) {
      axios.delete('http://89.88.140.151:8840/api/profile/' + id)
          .then(response => {
            console.log(response);
          })
          .catch(function (error) {
            console.log(error.profile)
          })

    },

    updateProfile(id) {
      axios.patch('http://89.88.140.151:8840/api/profile/' + id)
          .then(response => {
            console.log(response);
          })
          .catch(function (error) {
            console.log(error.profile)
          })
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
