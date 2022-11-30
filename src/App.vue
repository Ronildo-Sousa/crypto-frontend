<script setup>
import CoinPriceCard from './components/CoinPriceCard.vue'

const selectedCoin =  
    {
        "name": "Bitcoin",
        "symbol": "BTC",
        "date": "30-11-2022 14:08:15",
        "price": 16925.06
    }

// onMounted(() => axios.get("http://localhost/api/coins").then(response => {
//     coins.value = response.data
// }))
</script>

<template>
    <CoinPriceCard :coin="selectedCoin" />
</template>
