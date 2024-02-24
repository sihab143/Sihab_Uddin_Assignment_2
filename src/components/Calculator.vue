<script setup>
import { ref } from 'vue';

const num1 = ref(0);
const num2 = ref(0);
const operator = ref('+');
const result = ref(null);

const calculate = () => {
    switch (operator.value) {
        case '+':
            result.value = num1.value + num2.value;
            break;
        case '-':
            result.value = num1.value - num2.value;
            break;
        case '*':
            result.value = num1.value * num2.value;
            break;
        case '/':
            result.value = num1.value / num2.value;
            break;
        default:
            result.value = null;
    }
};
</script>
<template>
    <div>
        <input v-model="num1" type="number" placeholder="Enter number 1" />
        <input v-model="num2" type="number" placeholder="Enter number 2" />
        <select v-model="operator">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
        </select>
        <button @click="calculate">Calculate</button>
        <div v-if="result !== null">Result: {{ result }}</div>
    </div>
</template>