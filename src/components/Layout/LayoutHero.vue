<script setup>
defineProps({
  title: {
    type: String,
    default: 'GameStream',
  },
  subtitle: {
    type: String,
    default: 'Descubre y disfruta los mejores videojuegos en un solo lugar.',
  },
})
</script>

<template>
  <section class="hero">
    <div class="hero__content">
      <h1 class="hero__title">{{ title }}</h1>
      <h2 class="hero__subtitle">{{ subtitle }}</h2>
    </div>
  </section>
</template>

<style scoped>
.hero {
  background-color: var(--color-background-primary);
  background: linear-gradient(
    45deg,
    var(--color-background-primary) 0%,
    var(--color-background-secondary) 90%
  );
  padding: 2rem;
  text-align: center;
  color: var(--color-primary);
}

.hero h2 {
  font-family: 'Inter', serif;
  font-weight: 300;
}

.hero h1 {
  font-size: 2.5rem;
}
</style>
