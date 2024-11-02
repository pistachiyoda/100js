<script setup lang="ts">
defineProps({
    img: String,
    message: String,
});
</script>
<template>
    <div class="w-screen h-screen flex flex-col justify-center items-center ">
        <img :src="img" alt="avatar" width="100" height="auto" class="z-10 -mb-10" />
        <p class="w-[540px] h-[240px] px-[20px] py-[70x] bg-sky-300 shadow-xl flex items-center rounded-xl z-0">
            {{ message }}
        </p>
    </div>
</template>