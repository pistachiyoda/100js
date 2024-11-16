<script setup lang="ts">
defineProps<{
    label: string;
    id: string;
    modelValue: number;
}>();

const emit = defineEmits<{
    'update:modelValue': [value: number];
}>();
const update = (event: Event) => {
    const input = event.target as HTMLInputElement;
    emit('update:modelValue', input.valueAsNumber);
};
</script>
<template>
    <label :for="id">{{ label }} :</label>
    <input type="number" :id="id" :value="modelValue" @input="update" min="0" aria-label="label"
        class="border border-gray-300 rounded p-2" />
</template>