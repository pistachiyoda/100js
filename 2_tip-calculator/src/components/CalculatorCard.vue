<script setup lang="ts">
import { ref } from 'vue';
import FormInputField from './FormInputField.vue';

const billAmount = ref(0);
const tipPercentage = ref(0);
const total = ref(0);
const calcTotal = () => {
    const bill = billAmount.value;
    const tip = tipPercentage.value / 100;
    console.log(bill, tip);
    total.value = bill + (bill * tip);
};
</script>
<template>
    <div class="bg-white w-[600px] flex p-5  rounded-lg shadow-lg flex-col gap-3">
        <h1 class="font-semibold text-4xl text-center">
            Tip Calculator
        </h1>
        <p>
            Enter the bill amount and tip percentage to calculate the total.
        </p>
        <div class="flex flex-col gap-2">
            <FormInputField id="bill_amount" label="Bill Amount" v-model="billAmount" />
            <FormInputField id="tip_percentage" label="Tip Percentage" v-model="tipPercentage" />
        </div>
        <button @click="calcTotal" class="bg-green-500 text-white py-2 rounded-sm text-xl">Calculate</button>
        <p>Total: {{ total }}</p>
    </div>
</template>