<script setup lang="ts">
import { ref, computed, onUnmounted } from 'vue';

const time = 65;
const totalSeconds = ref(time);
const intervalId = ref<ReturnType<typeof setInterval>>();
const isCounting = ref(false);
const isEnd = ref(false);

const padZero = (num: number): string => {
    return num.toString().padStart(2, '0');
}

const minutesCnt = computed(() => {
    return padZero(Math.floor(totalSeconds.value / 60));
})
const secondsCnt = computed(() => {
    return padZero(totalSeconds.value % 60);
})

const start = () => {
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
    <div class="flex flex-col gap-12 items-center ">
        <header>
            <h1 class="font-semibold text-5xl mt-8">Pomodoro Timer</h1>
        </header>
        <div v-if="isEnd">終わった</div>
        <div class="flex font-semibold text-8xl">
            <div>{{ minutesCnt }}</div>
            <span>:</span>
            <div>{{ secondsCnt }}</div>
        </div>
        <div class="flex gap-6 text-white text-xl">
            <button @click="start" :disabled="isCounting"
                :class="[isCounting ? 'bg-green-300' : 'bg-green-600', 'px-5', 'py-3', 'rounded-sm']">START</button>
            <button @click="stop" class="bg-red-500  px-5 py-3 rounded-sm">STOP</button>
            <button @click="reset" class="bg-gray-500  px-5 py-3 rounded-sm">RESET</button>
        </div>
    </div>
</template>