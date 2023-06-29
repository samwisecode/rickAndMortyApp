<script setup>
import axios from 'axios'
import { ref, watch, onMounted } from 'vue'
import Card from './Card.vue'

const characters = ref(null)
const page = ref(1)


onMounted(async () => {
    const response = await axios.get('https://rickandmortyapi.com/api/character?page=1')
    characters.value = [...response.data.results]
})


watch(page, async () => {
    const res = await axios.get(`https://rickandmortyapi.com/api/character?page=${page.value}`)
    characters.value = [...res.data.results]
})


</script>

<template>
    <h1>Rick and Morty</h1>
    <div class="container">
        <div class="cards">
            <Card
                v-for="character in characters"
                :key="character.id"
                :image="character.image"
                :name="character.name"
                :episode="character.episode"
            >
                <div>
                    <p>{{ character.location.name }}</p>
                    <span>{{ character.episode.length }} episode</span>
                    <span v-if="character.episode.length > 1">s</span>
                </div>
            </Card>
        </div>
        <n-button type="info" @click="page = page - 1" :disabled="page == 1">Previous</n-button>
        <n-button type="info" @click="page = page + 1">Next</n-button>
    </div>
</template>

<style scoped>
h1 {
    text-align: center;
}
.container {
    background-color: rgb(27, 26, 26);
    padding: 30px
}
.cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
}
.cards h3 {
    font-weight: bold;
}
.cards p {
    font-size: 10px;
}

.button-container {
    display: flex;
    justify-content: center;
    padding-top: 30px
}
.button-container button {
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin: 0 5px;
    cursor: pointer;
}
</style>