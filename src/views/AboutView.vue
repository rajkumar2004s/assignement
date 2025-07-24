<script setup>
import { ref, computed } from 'vue'
import ReviewForm from './ReviewForm.vue'
import ReviewsList from './ReviewsList.vue'
const brand = ref('Vue Mastery')
const product = ref('Socks')
const blueSocks =
  'https://assets.myntassets.com/w_412,q_60,dpr_2,fl_progressive/assets/images/16773414/2022/1/11/6ac76cba-4b31-4d7f-a953-ace61cfb36071641877813181Socks1.jpg'
const whiteSocks =
  'https://assets.ajio.com/medias/sys_master/root/20240726/Ygp0/66a3c1601d763220fa3768a9/-473Wx593H-465406731-white-MODEL.jpg'

function clickme() {
  selectedVariant.value = selectedVariant.value === 0 ? 1 : 0
}

const list = ['Cotton', 'Nylon', 'Woolen', 'howlee']
const Details = ref(list)

const emit = defineEmits(['add-to-cart'])
function addToCart() {
  emit('add-to-cart', variants.value[selectedVariant.value].id)
}

const title = computed(() => {
  return brand.value + ' ' + product.value
})

const variants = ref([
  { id: 1789, color: 'Blue', image: blueSocks, quantity: 50 },
  { id: 2637, color: 'white', image: whiteSocks, quantity: 0 },
])

const selectedVariant = ref(0)
const image = computed(() => {
  return variants.value[selectedVariant.value].image
})
const instock = computed(() => {
  return variants.value[selectedVariant.value].quantity > 0
})

const updateVariant = (index) => {
  selectedVariant.value = index
}

const props = defineProps(['premium'])
const shipping = computed(() => {
  if (props.premium) {
    return 'Free'
  } else {
    return '2.99'
  }
})

const reviews = ref([])
const addReview = (review) => {
  reviews.value.push(review)
}
</script>

<template>
  <div class="card">
    <div>
      <h1>{{ title }}</h1>
      <img :src="image" width="200" />
      <button class="b" @click="clickme">Click me</button>
      <p v-if="instock">In Stock</p>

      <p v-else>Out of Stock</p>
      <ul>
        <li v-for="(detail, index) in Details" :key="index">{{ detail }}</li>
      </ul>
      <p>Shipping: {{ shipping }}</p>
      <ul>
        <li
          :style="{ backgroundColor: variant.color }"
          class="color-bg"
          v-for="(variant, index) in variants"
          :key="variant.id"
          @mouseover="updateVariant(index)"
        >
          {{ variant.color }}
        </li>
      </ul>

      <button class="b" :disabled="!instock" v-on:click="addToCart">Add to Cart</button>
    </div>
    <div class="p">
      <ReviewsList v-if="reviews.length > 0" :reviews="reviews"></ReviewsList>
      <ReviewForm @review-submitted="addReview"></ReviewForm>
    </div>
  </div>
</template>

<style scoped>
.card {
  display: flex;
}
.p {
  margin-right: 100px;
}
</style>
