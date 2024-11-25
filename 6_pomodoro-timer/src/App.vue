<script setup lang="ts">
import { ref, computed, onUnmounted } from 'vue';

const time = 1500;
const totalSeconds = ref(time);
const intervalId = ref<ReturnType<typeof setInterval>>();
const isCounting = ref(false);
const isEnd = ref(false);

const minutesCnt = computed(() => {
    return Math.floor(totalSeconds.value / 60).toString().length <= 1 ? `0${Math.floor(totalSeconds.value / 60)}` : Math.floor(totalSeconds.value / 60);
})
const secondsCnt = computed(() => {
    return (totalSeconds.value % 60).toString().length <= 1 ? `0${(totalSeconds.value % 60).toString()}` : (totalSeconds.value % 60).toString();
})

const start = () => {
    if (isCounting.value) return;
    isCounting.value = true;
    intervalId.value = setInterval(() => {
        totalSeconds.value--;
        if (totalSeconds.value <= 0) {
            isEnd.value = true;
            clearInterval(intervalId.value);
        }
    }, 1000)
}

const stop = () => {
    clearInterval(intervalId.value);
    isCounting.value = false;
}

const reset = () => {
    clearInterval(intervalId.value);
    totalSeconds.value = time;
    isCounting.value = false;
}

onUnmounted(() => clearInterval(intervalId.value))

</script>

<template>
    <header>
        <h1>Pomodoro Timer</h1>
    </header>
    <div v-if="isEnd">終わった</div>
    <div class="flex">
        <div>{{ minutesCnt }}</div>
        <span>:</span>
        <div>{{ secondsCnt }}</div>
    </div>
    <div class="flex gap-2">
        <button @click="start">START</button>
        <button @click="stop">STOP</button>
        <button @click="reset">RESET</button>
    </div>
</template>