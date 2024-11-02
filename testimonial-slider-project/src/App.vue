<script setup lang="ts">
import TestimonialCard from './components/TestimonialCard.vue';
import { ref } from 'vue';

const currentIndex = ref(0);
setInterval(() => {
  if (currentIndex.value === testimonials.length - 1) {
    currentIndex.value = 0;
  } else {
    currentIndex.value += 1;
  }
}, 2000);

const testimonials = [
  {
    id: 1,
    img: '/review_woman_star5.png',
    message: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
  },
  {
    id: 2,
    img: '/review_woman_star4.png',
    message: 'Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
  },
  {
    id: 3,
    img: '/review_woman_star3.png',
    message: 'Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
  }
]


</script>

<template>
  <header></header>
  <main>
    <TestimonialCard :img="testimonials[currentIndex].img" :message="testimonials[currentIndex].message" />
  </main>
</template>
