<template>
  <div class="login-container">
    <div class="login-form">
      <h2 class="text-center mb-4">Welcome Back!</h2>
      <form @submit.prevent="login">
        <div class="mb-3">
          <label for="username" class="form-label">Username</label>
          <input type="text" class="form-control" id="username" v-model="username" required>
        </div>
        <div class="mb-3">
          <label for="password" class="form-label">Password</label>
          <input type="password" class="form-control" id="password" v-model="password" >
        </div>
        <button type="submit" class="btn btn-primary w-100">Login</button>
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
import {ref} from "vue";
import axiosInstance from '../utils/request';

const username = ref("")
const password = ref(null)

const login = async () => {
  await axiosInstance.post('/login',{
    username: username.value,
    password: password.value
  }).then((response)=>{
    const user = response.data
    console.log(user)
    if(user.role)  window.location.assign('http://localhost:3000/admin-home?userId=' + user.id)
    else window.location.assign('http://localhost:3000/user-home?userId=' + user.id)
  }) .catch((e) => {
    console.log(e)
    alert(e)
  })
}


</script>


<style scoped>
.login-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.login-form {
  max-width: 400px;
  width: 100%;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.form-label {
  font-weight: bold;
}

.btn-primary {
  background-color: #007bff;
  border-color: #007bff;
}

.btn-primary:hover {
  background-color: #0056b3;
  border-color: #0056b3;
}
</style>
