<script setup lang="ts">
defineProps<{
    label: string;
    id: string;
    modelValue: string;
}>();

const emit = defineEmits(['update:modelValue']);
const update = (event: Event) => {
    const input = event.target as HTMLInputElement;
    emit('update:modelValue', input.value);
};
</script>
<template>
    <label for="{{ id }}">{{ label }}</label>
    <input type="text" id="{{ id }}" @input="update" />
</template>