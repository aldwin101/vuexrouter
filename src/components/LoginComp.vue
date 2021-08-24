<template>
  <div class="hello">
      <input v-model="email" type="text" placeholder="email">
      <input v-model="password" type="password" placeholder="password">
      <button @click="makeLogInCall">Log in</button>
  </div>
</template>

<script>
import axios from 'axios'
import cookies from 'vue-cookies'

export default {
  name: 'LoginComp',
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    makeLogInCall(){
      axios.request ({
          url : 'https://reqres.in/api/login',
          method : 'POST',
          headers : {
              'Content-Type': 'application/json'
          },
          data : {
              'email': this.email,
              'password': this.password
          }
      }).then((response) => {
          cookies.set('logInToken',response.data.token)
          this.$router.push({name: 'About'});
      }).catch((error) => {
          console.error(error);
      })
  },
  }
}
</script>

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
