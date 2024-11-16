<script setup lang="ts">
import { ref, computed } from 'vue';
const birthdate = ref<string>('');
const calcAge = computed(() => {
  const diffSec = Math.floor((new Date().getTime() - new Date(birthdate.value).getTime()) / 1000); //秒
  const age = Math.floor(diffSec / 3600 / 24 / 365);
  return age;
})
</script>

<template>
  <main>
    <div>
      <h1>Age Calculator</h1>
      <label for="birthdate">Enter your birthdate</label>
      <input type="date" id="birthdate" v-model="birthdate" />
    </div>
    <div>Your age is {{ calcAge }} years old</div>
  </main>
</template>