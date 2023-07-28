<template>
  <NuxtLink :to="props.to"
    class="flex select-none flex-col justify-center items-center p-2 active:text-lime-400 focus:text-lime-400 focus:bg-gray-500 transition-all">
    <Icon :name="props.icon" size="1.3rem" :color="color" />
    <span>{{ props.text }}</span>
  </NuxtLink>
</template>

<script setup>

const props = defineProps(['to', 'text', 'icon', 'color'])
</script>