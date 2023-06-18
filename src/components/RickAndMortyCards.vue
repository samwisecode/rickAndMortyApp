<script setup>
import axios from 'axios'
import { ref, watch } from 'vue'

const characters = ref(null)
const page = ref(0)

const response = await  axios.get('https://rickandmortyapi.com/api/character?page=1')
characters.value = response.data.results

watch(page, async () => {
    const res = await axios.get(`https://rickandmortyapi.com/api/character?page=${page.value * 20}`)
})
</script>

<template>
    <div>
        <h1>Rick and Morty Cards</h1>
        <div>{{ response.data.results }}</div>
        <button @click="page = page--">
            Previous
        </button>
        <button @click="page = page++">
            Next
        </button>
    </div>
</template>