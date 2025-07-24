<template>
  <div>
    <h1 :class="toggle ? 'green' : 'red'">Ternery Styling</h1>
    <button @click="toggleColor">Toggle Color</button>

    <div :class="{ blueColor: blue, pink: color }">
      <p>Object styling</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const blue = ref(true)
const color = ref(false)
const toggle = ref(false)

const toggleColor = () => {
  toggle.value = !toggle.value
}
</script>

<style scoped>
.blueColor {
  color: blue;
  font-weight: bold;
  font-size: 20px;
}
.pink {
  color: rgb(246, 7, 47);
  font-weight: bold;
  font-size: 20px;
}

.green {
  color: green;
}
.red {
  color: red;
}
.green-color {
  color: darkgreen;
}
</style>
