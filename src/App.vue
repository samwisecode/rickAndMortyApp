<script setup>
import TvShowCards from '@/components/TvShowCards.vue';
import Hero from '@/components/Hero.vue';
</script>

<template>
  <main>
    <Hero />
    <Suspense>
      <template #default>
        <KeepAlive>
          <Component :is="TvShowCards" />
        </KeepAlive>
      </template>
      <template #fallback>
        <div class="cards spinner">
          <n-space>
            <n-spin size="large" />
          </n-space>
        </div>
      </template>
    </Suspense>
  </main>
</template>

<style scoped>
.cards {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
