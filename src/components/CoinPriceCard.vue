<script setup>
import { computed } from 'vue'

const props = defineProps({
    coin: Object
})

</script>

<template>
    <section class="flex flex-col items-center max-w-sm p-3 border border-gray-300 rounded-md shadow-md">
        <div class="flex justify-around w-full mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                stroke="currentColor" class="w-6 h-6 text-green-500">
                <path stroke-linecap="round" stroke-linejoin="round"
                    d="M12 6v12m-3-2.818l.879.659c1.171.879 3.07.879 4.242 0 1.172-.879 1.172-2.303 0-3.182C13.536 12.219 12.768 12 12 12c-.725 0-1.45-.22-2.003-.659-1.106-.879-1.106-2.303 0-3.182s2.9-.879 4.006 0l.415.33M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
            <h1 class="mr-3 text-2xl font-semibold">{{ coin.name }}</h1>
            <span>{{ coin.symbol }}</span>
        </div>
        <p class="mb-3 text-3xl font-bold">$ {{ coin.price }}</p>
        <p>{{ coin.date }}</p>
    </section>
</template>