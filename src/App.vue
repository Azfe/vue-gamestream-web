<script setup>
// import LayoutHero from "@/components/Layout/LayoutHero.vue";
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
  const gamesData = await fetchGames()
  state.data.push(...gamesData)
})

</script>

<template>
  <!-- <LayoutHero /> -->
  <main></main>
</template>

<style scoped>
main {
  padding: 2rem;
}

</style>
