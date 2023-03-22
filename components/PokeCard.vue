<template>
  <NuxtLink
    :to="`pokemon/${pokemon.id}`"
    class="text-center flex flex-col border border-neutral-800 rounded-xl p-3 hover:scale-105 cursor-pointer transition"
  >
    <img :src="pokemon.image" :alt="pokemon.name" />
    <p class="text-sm capitalize text-neutral-400 font-medium">
      {{ pokemon.name }}
    </p>
  </NuxtLink>
</template>

<script setup>
const { pokemon } = defineProps(["pokemon"])
</script>
