<template>
  <header>
    <h2 class="text-xl font-bold text-center">{{ title }}</h2>
    <p>{{ description }}</p>
  </header>
</template>

<script setup>
const { title, description } = defineProps(['title', 'description'])
</script>