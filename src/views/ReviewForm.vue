<script setup>
import { reactive } from 'vue'

const review = reactive({
  name: '',
  content: '',
  rating: null,
})

const emit = defineEmits(['review-submitted'])

const onSubmit = () => {
  if (review.name === '' || review.content === '' || review.rating === null) {
    alert('Fill all the details')
    return
  }

  const productReview = {
    name: review.name,
    content: review.content,
    rating: review.rating,
  }
  emit('review-submitted', productReview)

  // Reset form
  review.name = ''
  review.content = ''
  review.rating = null
}
</script>

<template>
  <form @submit.prevent="onSubmit">
    <h3>Leave a Review</h3>
    <label for="name">Name:</label>
    <input id="name" v-model="review.name" />

    <label for="review">Review:</label>
    <textarea id="review" v-model="review.content"></textarea>

    <label for="rating">Rating:</label>
    <select id="rating" v-model.number="review.rating">
      <option>5</option>
      <option>4</option>
      <option>3</option>
      <option>2</option>
      <option>1</option>
    </select>

    <input class="button" type="submit" value="Submit" />
  </form>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-top: 20px;
}
</style>
