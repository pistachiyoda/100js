<script setup lang="ts">
import { ref } from 'vue';
import FormInputField from './FormInputField.vue';

const billAmount = ref('');
const tipPercentage = ref('');
const total = ref(0);
const calcTotal = () => {
    const bill = parseFloat(billAmount.value);
    const tip = parseFloat(tipPercentage.value) / 100;
    total.value = bill + (bill * tip);
};
</script>
<template>
    <h1>
        Tip Calculator
    </h1>
    <p>
        Enter the bill amount and tip percentage to calculate the total.
    </p>
    <FormInputField id="bill_amount" label="Bill Amount" v-model="billAmount" />
    <FormInputField id="tip_percentage" label="Tip Percentage" v-model="tipPercentage" />
    <button @click="calcTotal">Calculate</button>
    <p>Total: {{ total }}</p>
</template>