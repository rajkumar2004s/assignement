<template>
  <div>
    <h1>Welcome to home page</h1>
    <div>
      <TypeToggle />
    </div>

    <div>
      <ClassBinding />
    </div>
  </div>
</template>

<script setup>
import TypeToggle from '../components/TypeToggle.vue'
import ClassBinding from './ClassBinding.vue'
</script>

<style scoped>
h1 {
  font-size: 40px;
}
</style>
