<script setup>
defineProps({
  reviews: {
    type: Array,
    required: true,
  },
})
</script>

<template>
  <div>
    <h3>Reviews:</h3>
    <ul>
      <li v-for="(review, index) in reviews" :key="index">
        <span> {{ review.name }} gave this {{ review.rating }} stars </span>
        <br />
        <span>{{ review.content }}</span>
      </li>
    </ul>
  </div>
</template>
