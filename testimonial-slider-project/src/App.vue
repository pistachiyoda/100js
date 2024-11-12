<script setup lang="ts">
import TestimonialCard from './components/TestimonialCard.vue';
import { onUnmounted, ref } from 'vue';

const currentIndex = ref(0);
const intervalId = setInterval(() => {
  if (currentIndex.value === testimonials.length - 1) {
    currentIndex.value = 0;
  } else {
    currentIndex.value += 1;
  }
}, 2000);

onUnmounted(() => {
  clearInterval(intervalId);
});

interface Testimonial {
  id: number;
  img: string;
  message: string;
}

const testimonials: Testimonial[] = [
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
    message: 'Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
  }
]


</script>

<template>
  <main class="h-screen flex flex-col justify-center items-center">
    <template v-if="testimonials.length">
      <TestimonialCard :img="testimonials[currentIndex].img" :message="testimonials[currentIndex].message" />
    </template>
    <template v-else>
      <p>Testimonials not found</p>
    </template>
  </main>
</template>
