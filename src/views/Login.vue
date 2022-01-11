// login view
<template>
  <div class="login">
    <form @submit.prevent="login">
      <div class="form-group">
        <input type="email" id="email" placeholder="Email" v-model="email" class="form-control">
      </div>
      <div class="form-group">
        <input type="password" id="password" placeholder="Password" v-model="password" class="form-control">
      </div>
      <router-link to="/password-recovery">Forgot your password?</router-link>
      <button class="btn btn-primary">Login</button>
    </form>
    <div class="separator"></div>
    <form @submit.prevent="register">
      <button class="btn btn-secondary">Register</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    login() {
      axios.post('/login', {
        email: this.email,
        password: this.password
      })
      .then(response => {
        console.log(response);
      })
      .catch(error => {
        console.log(error);
      });
    },
    register() {
      this.$router.push('/register')
    }
  }
}
</script>

<style scoped>
  .login {
    display: flex;
    flex-direction: column;
    width: 300px;
    margin: 0 auto;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 20px; 
  }
  
  .login * {
    margin-top: 10px;
  }

  .login form {
    display: flex;
    flex-direction: column;
  }

  .separator {
    margin-top: 20px;
    border-top: 1px solid #ccc;
  }

  input, button {
    padding: 0;
    width: 300px;
    height: 30px;
  }
</style>
