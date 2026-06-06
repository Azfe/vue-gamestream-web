<script setup>
import LayoutHero from "@/components/Layout/LayoutHero.vue";
import GameCard from "@/components/Games/GameCard.vue";
import { onMounted, reactive } from 'vue'

const API_URL = 'https://gamestreamapi.herokuapp.com/api/games'

const state = reactive({
  error: null,
  isLoading: false,
  data: []
})

const fetchGames = async () => {
  try {
    state.isLoading = true
    const response = await fetch(API_URL)
    const json = await response.json()
    state.data = json
    return state.data
  } catch (error) {
    state.error = error
  } finally {
    state.isLoading = false
  }
}

onMounted(async () => {
  await fetchGames()
})

</script>

<template>
  <LayoutHero />
  <main>
    <!-- <GameLayout :games="state.data" /> -->
    <GameCard v-for="game in state.data" :key="game.title" :game="game" />
  </main>
</template>

<style scoped>
main {
  padding: 2rem;
}

</style>
