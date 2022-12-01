<script setup>
import { ref, watch, onBeforeMount } from 'vue'
import axios from 'axios'
import CoinPriceCard from './components/CoinPriceCard.vue'

const BASE_URL = "http://localhost/api/"

const coins = ref([
    {
        "id": 1,
        "symbol": "BTC",
        "identifier": "bitcoin"
    },
    {
        "id": 2,
        "symbol": "ATOM",
        "identifier": "cosmos"
    },
])

const getRecentPrice = (coin) => {
    axios.get(BASE_URL + "price/" + coin).then((response) => {
        coinInfo.value  = response.data.recent_price
    })
}

const getHistoryPrice = (coin) => {
    console.log(coin)
}

let coinInfo = ref(null)

const openDefaultMenu = ref(true)
const changeMenu = (value) => {
    openDefaultMenu.value = value
}

const selectedCoin = ref(coins.value[0].name)

watch(selectedCoin, () => {
    if (openDefaultMenu) {
        getRecentPrice(selectedCoin.value)
    }
})

onBeforeMount(() => {
    getRecentPrice("bitcoin")
})

// const selectedCoin =
// {
//     "name": "Bitcoin",
//     "symbol": "BTC",
//     "date": "30-11-2022 14:08:15",
//     "price": 16925.06
// }
</script>

<template>
    <main class="text-center">
        <header class="flex items-center justify-center h-16 bg-green-400">
            <h1 class="text-2xl font-bold">Crypto App</h1>
        </header>
        <div class="mt-3 mb-3">
            <button @click="changeMenu(true)" :class="{'underline': openDefaultMenu}" class="text-lg">
                Recent price
            </button>
            <span class="mx-8 text-gray-300">|</span>
            <button @click="changeMenu(false)" :class="{ 'underline': !openDefaultMenu }" class="text-lg">
                History price
            </button>
        </div>
        <div class="flex justify-center">
            <div v-if="openDefaultMenu" class="flex items-center justify-around w-full max-w-md mt-8 mb-8 md:w-3/4">
                <span>Get recent price of: </span>
                <select v-model="selectedCoin" id="coins" class="w-2/4 p-1 shadow-lg rounde-md">
                    <option v-for="coin in coins" :value="coin.identifier" :key="coin.id">{{ coin.symbol }}</option>
                </select>
            </div>
            <div v-else>
                menu 2
            </div>
        </div>
        <div class="flex items-center justify-center">
            <CoinPriceCard class="w-full" :coin="coinInfo" />
        </div>
    </main>
</template>
