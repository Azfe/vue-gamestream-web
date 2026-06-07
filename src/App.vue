<script setup>
import { onMounted, reactive, ref } from 'vue'
import LayoutHero from "@/components/Layout/LayoutHero.vue";
import GameLayout from "@/components/Games/GameLayout.vue";
import GameCard from "@/components/Games/GameCard.vue"
import GameModal from "@/components/Games/GameModal.vue";
import SharedLoader from "@/components/Shared/SharedLoader.vue";

const API_URL = 'https://gamestreamapi.herokuapp.com/api/games'

const gamesView = ref([])

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
    gamesView.value = json
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

const setGameView = (filteredGames) => {
  gamesView.value = filteredGames
}

</script>

<template>
  <LayoutHero />
  <main>
    <SharedLoader v-if="state.isLoading" />
    <GameLayout v-else :games="state.data" @set-game-view="setGameView">
      <GameCard v-for="game in gamesView" :key="game.title" :game="game" />
    </GameLayout>
    <Teleport to="body">
      <GameModal />
    </Teleport>
  </main>
</template>

<style scoped>
main {
  padding: 2rem;
}
</style>
