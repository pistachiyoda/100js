<script setup lang="ts">
import RecipeCard from './components/RecipeCard.vue';
import { Recipe } from './types';
import axios from 'axios';
import { onMounted, ref } from 'vue';


const recipes = ref<Recipe[]>([]);
const applicationId = import.meta.env.VITE_APPLICATION_ID;

const fetchRecipes = async function () {
    try {
        const res = await axios.get(`https://app.rakuten.co.jp/services/api/Recipe/CategoryRanking/20170426?format=json&applicationId=${applicationId}`);
        recipes.value = res.data.result;
        console.log(recipes.value);
    } catch (err) {
        console.error(err);
    }
}
onMounted(() => {
    fetchRecipes();
})
</script>

<template>
    <header class="bg-orange-600 text-white text-center font-bold text-4xl py-5 mb-6">
        <h1>Recipe Book App</h1>
    </header>
    <main>
        <ul class="flex flex-col gap-4 items-center">
            <li v-for="recipe in recipes" :key="recipe.recipeId">
                <RecipeCard :recipe="recipe" />
            </li>
        </ul>
    </main>
</template>