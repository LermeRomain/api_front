<template>
  <div>
    <h1>Créations user</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="name">Name:</label><br>
        <input id="name" type="text" v-model="name" required/>
      </div>
      <div>
        <label for="surname">Surname:</label><br>
        <input id="surname" type="text" v-model="username" required/>
      </div>
      <div>
        <label for="phone">phone:</label><br>
        <input id="phone" type="text" v-model="phone" required/>
      </div>
      <div>
        <label for="company">company:</label><br>
        <input id="company" type="text" v-model="company" required/>
      </div>
      <button :class="[name ? activeClass : '']" type="submit">Submit</button>
    </form>

  </div>
</template>

<script>

import axios from "axios";

export default {

  // eslint-disable-next-line vue/multi-word-component-names
  name: "Create",
  data() {
    return {
      companys: null,
      name: '',
      username: '',
      phone: '',
      company: '',
      activeClass: 'active'
    }
  },
  methods: {
    submitForm() {
      axios.post('http://89.88.140.151:8840/api/profile/', {
        name: this.name,
        surname: this.username,
        phone: this.phone,
        company: this.company
      }).then(response => {
        console.log(response);
        this.response = response.data
        this.response = JSON.stringify(response, null, 2)
      }).catch(error => {
        this.response = 'Error: ' + error.response.status
      })
      this.name = '';
      this.surname = '';
      this.phone = '';
      this.company = '';
    }
  },
}
</script>

<style scoped>

</style>