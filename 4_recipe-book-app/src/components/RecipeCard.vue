<script setup lang="ts">
import { Recipe } from '../types';
defineProps<{
    recipe: Recipe;
}>();
</script>
<template>
    <div class="flex items-center gap-4 w-full bg-white shadow-md">
        <img :src="recipe.foodImageUrl" alt="Food image" class=" w-[150px] h-[150px] object-cover" loading="lazy">
        <h2 class="max-w-60 font-bold text-lg">{{ recipe.recipeTitle }}</h2>
        <p class="w-[700px] text-gray-600">
            {{ recipe.recipeDescription }}
        </p>
        <a class="bg-orange-200 py-3 px-5 w-40" :href="recipe.recipeUrl">
            View detail
        </a>
    </div>
</template>