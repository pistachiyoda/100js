<script setup lang="ts">
defineProps({
    img: String,
    message: String,
});
</script>
<template>
    <div class="flex flex-col justify-center items-center ">
        <img :src="img" :alt="`Testimonial author's avatar`" width="100" height="auto" class="z-10 -mb-10 object-cover"
            @error="console.log('画像読み込み失敗')" loading="lazy" />
        <p class="w-[540px] h-[240px] px-[20px] py-[70px] bg-sky-300 shadow-xl flex items-center rounded-xl z-0">
            <span class="overflow-y-auto max-h-[200px] text-gray-800">
                {{ message }}
            </span>
        </p>
    </div>
</template>