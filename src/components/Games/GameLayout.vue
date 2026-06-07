<script setup>
import { ref, useSlots } from 'vue'
import SharedSearch from '@/components/Shared/SharedSearch.vue'

const slots = useSlots()
// console.log(slots.title)
const searchInput = ref('')

const emit = defineEmits(['setGameView'])

const { games } = defineProps({
  games: {
    type: Array,
    required: true,
  },
})

/* Evento para buscar juegos */
const onSearch = () => {
  const termSearch = searchInput.value.toLowerCase()

  if (termSearch.trim() === '') {
    emit('setGameView', games)
    return
  }

  const filteredGames = games.filter((game) => {
    return game.title.toLowerCase().includes(termSearch)
  })

  emit('setGameView', filteredGames)
}
</script>

<template>
  <section>
    <slot name="title" />
    <h2 v-if="!slots.title" style="text-align: center">Juegos recientes</h2>
    <SharedSearch @search="onSearch" v-model="searchInput" id="probando" />
    <div class="game-layout">
      <slot />
    </div>
  </section>
</template>

<style scoped>
.game-layout {
  display: grid;
  gap: 2rem;
  margin: 1rem auto;
  max-width: 65%;
}
</style>
