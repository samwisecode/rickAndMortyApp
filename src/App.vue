<script setup>
import RickAndMortyCardsVue from './components/RickAndMortyCards.vue'
</script>

<template>
  <main>
    <Suspense>
      <template #default>
        <RickAndMortyCardsVue />
      </template>
      <template #fallback>
        <div>Loading...</div>
      </template>
    </Suspense>
  </main>
</template>

<style scoped>
</style>
