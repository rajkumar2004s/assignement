<template>
  <div>
    <h3>Check here hide and show password</h3>
    <input :type="showPassword ? 'text' : 'password'" placeholder="Password" />
    <button @click="toggle">{{ showPassword ? 'Hide' : 'Show' }}</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const showPassword = ref(false)

const toggle = () => {
  showPassword.value = !showPassword.value
}
</script>
