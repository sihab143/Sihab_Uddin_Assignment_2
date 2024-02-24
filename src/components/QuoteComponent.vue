<script setup>
import { ref } from 'vue';
import axios from 'axios';

const quote = ref(null);

const fetchQuote = async () => {
    try {
        const response = await axios.get('https://animechan.xyz/api/random');
        quote.value = response.data;
    } catch (error) {
        console.error('Error fetching quote:', error);
    }
};
</script>
<template>
    <div>
        <h2>Random Anime Quote</h2>
        <button @click="fetchQuote">Get Quote</button>
        <div v-if="quote">
            <p><strong>Quote:</strong> {{ quote.quote }}</p>
            <p><strong>Anime:</strong> {{ quote.anime }}</p>
            <p><strong>Character:</strong> {{ quote.character }}</p>
        </div>
    </div>
</template>