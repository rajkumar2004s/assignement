<template>
  <div>
    <input v-model="username" placeholder="Enter your name" />
    <input v-model="age" placeholder="Age" />
    <input v-model="mail" placeholder="E-mail" @keyup.enter="Login" />
    <button @click="Login">Login</button>

    <p class="para" v-if="error">{{ error }}</p>

    <div>
      <p>Demo Data</p>
      <p>username : rajkumar</p>
      <p>age : 20</p>
      <p>raju@gmail.com</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const username = ref('')
const age = ref('')
const mail = ref('')
const error = ref('')
const router = useRouter()

const Login = () => {
  if (
    username.value.toLowerCase() === 'rajkumar' &&
    age.value === '20' &&
    mail.value.toLowerCase() === 'raju@gmail.com'
  ) {
    router.push('/home')
  } else {
    error.value = 'Please Enter Valid Credentials ..'
  }
}
</script>

<style scoped>
.para {
  color: red;
  font-weight: bold;
  font-size: 18px;
}
</style>
