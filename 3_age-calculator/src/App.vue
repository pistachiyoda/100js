<script setup lang="ts">
import { ref, computed } from 'vue';
const birthdate = ref<string>('');
const calcAge = computed(() => {
  const diffSec = Math.floor((new Date().getTime() - new Date(birthdate.value).getTime()) / 1000);
  const age = Math.floor(diffSec / 3600 / 24 / 365);
  return age;
})
</script>

<template>
  <main class="h-screen w-screen flex flex-col justify-center items-center">
    <div class="w-[600px] bg-white rounded-md shadow-md p-5 text-center flex flex-col gap-8">
      <h1 class="font-semibold text-4xl">Age Calculator</h1>
      <div class="flex flex-col gap-4 items-center">
        <label for="birthdate" class="font-semibold text-xl">Enter your birthdate</label>
        <input type="date" id="birthdate" :max="new Date().toISOString().split('T')[0]" v-model="birthdate" required
          class="w-1/2 border border-gray-300 rounded p-2" />
      </div>
      <p class="font-semibold text-2xl">Your age is {{ isNaN(calcAge) ? "?" : calcAge }} years old</p>
    </div>
  </main>
</template>