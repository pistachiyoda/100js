<script setup lang="ts">
import { Dice } from '@/type';

defineProps<{
    id: number;
    dice: Dice;
}>();

</script>
<template>
    <div class="bg-gray-200 w-96 flex items-center justify-between px-5 shadow-lg rounded-lg">
        <div class="text-2xl">
            Roll {{ id + 1 }}
        </div>
        <div class="text-6xl">
            {{ dice }}
        </div>
    </div>
</template>