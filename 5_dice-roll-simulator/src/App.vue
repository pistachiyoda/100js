<script setup lang="ts">
import ResultCard from './components/ResultCard.vue';
import { ref } from 'vue';
import { Dice } from './type'

const dices: Dice[] = ['⚀', '⚁', '⚂', '⚃', '⚄', '⚅'];
const isRolling = ref(false);
const diceHistory = ref<Dice[]>([])
const rollDice = () => {
    isRolling.value = true;
    setTimeout(() => {
        isRolling.value = false;
        diceHistory.value.push(dices[Math.floor(Math.random() * 5)]);
        console.log(diceHistory)
    }, 1500)
}
</script>

<template>
    <header>
        <h1 class="font-semibold text-4xl text-center py-6">Dice Roll Simulator</h1>
    </header>
    <div class="flex flex-col w-full items-center">

        <div :class="[isRolling ? 'animate-spin' : '', 'text-8xl', 'mb-2']">
            {{ diceHistory[diceHistory.length - 1] || '⚀' }}
        </div>
        <button @click="rollDice" class="bg-blue-400 text-white rounded-xl py-3 mb-4 px-4 text-2xl">
            Roll Dice
        </button>
    </div>
    <div class="flex flex-col gap-4 items-center">
        <ResultCard v-for="(dice, index) in diceHistory" :key="index" :id="index" :dice="dice">
        </ResultCard>
    </div>
</template>