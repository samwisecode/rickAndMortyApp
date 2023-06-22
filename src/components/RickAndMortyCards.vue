<script setup>
import axios from 'axios'
import { ref, watch } from 'vue'

const characters = ref(null)
const page = ref(1)

characters.value = await axios.get('https://rickandmortyapi.com/api/character?page=1')

watch(page, async () => {
    const res = await axios.get(`https://rickandmortyapi.com/api/character?page=${page.value}`)
    characters.value = res.data.results
})
</script>

<template>
    <div>
        <h1>Rick and Morty Cards</h1>
        <button @click="page--">Previous</button>
        <button @click="page++">Next</button>
        <code>{{ characters }}</code>
    </div>
</template>