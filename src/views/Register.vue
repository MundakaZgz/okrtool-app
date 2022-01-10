<template>
<div class="register">
  <h1>Register</h1>
  <form @submit.prevent="register">
    <div class="form-group">
      <label for="name">Name</label>
      <input type="text" id="name" v-model="name" class="form-control">
    </div>
    <div class="form-group">
      <label for="email">Email</label>
      <input type="email" id="email" v-model="email" class="form-control">
    </div>
    <div class="form-group">
      <label for="password">Password</label>
      <input type="password" id="password" v-model="password" class="form-control">
    </div>
    <div class="form-group">
      <label for="password_confirmation">Password Confirmation</label>
      <input type="password" id="password_confirmation" v-model="password_confirmation" class="form-control">
    </div>
    <button class="btn btn-primary">Register</button>
  </form>
</div>
</template>

<script>
import axios from 'axios'
export default {
  setup() {
    return {
      name: '',
      email: '',
      password: '',
      password_confirmation: ''
    }
  },
  methods: {
    register() {
      axios.post('/register', {
        name: this.name,
        email: this.email,
        password: this.password,
        password_confirmation: this.password_confirmation
      })
      .then(response => {
        console.log(response);
      })
      .catch(error => {
        console.log(error);
      });
    }
  }
}
</script>