<template>
  <div class="password-recovery">
    <h1>Password Recovery</h1>
    <form @submit.prevent="recover">
      <div class="form-group">
        <label for="email">Email</label>
        <input type="email" id="email" v-model="email" class="form-control">
      </div>
      <button class="btn btn-primary">Recover</button>
    </form>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      email: ''
    }
  },
  methods: {
    recover() {
      axios.post('/password/recovery', {
        email: this.email
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
<style scoped>
.password-recovery {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>