<template>
  <div class="space-y-4">
    <div class="flex gap-4">
      <button @click="$router.go(-1)">
        <img src="/back.svg" alt="back" class="w-6 h-6 mb-6" />
      </button>
      <h1 class="text-2xl text-neutral-100 font-bold mb-8">Pokemon detail</h1>
    </div>
    <div class="flex justify-center">
      <div class="flex">
        <img :src="data.sprites.front_default" class="w-28 h-28 object-cover" />

        <div class="flex flex-col mr-5">
          <img
            :src="data.sprites.back_default"
            class="w-16 h-16 object-cover"
          />
          <img :src="data.sprites.front_shiny" class="w-16 h-16 object-cover" />
          <img :src="data.sprites.back_shiny" class="w-16 h-16 object-cover" />
        </div>
      </div>
      <div
        class="border border-neutral-600 rounded-xl p-5 text-xs flex-1 max-w-[300px]"
      >
        <p class="text-sm font-bold text-neutral-300">Name :</p>
        <p class="text-neutral-200 capitalize mb-3">{{ data.name }}</p>

        <p class="text-sm font-bold text-neutral-300">Height</p>
        <p class="text-neutral-200 capitalize mb-3">{{ data.height }}</p>

        <p class="text-sm font-bold text-neutral-300">Base experience:</p>
        <p class="text-neutral-200 capitalize mb-3">
          {{ data.base_experience }}
        </p>

        <p class="text-sm font-bold text-neutral-300">Weight</p>
        <p class="text-neutral-200 capitalize mb-3">{{ data.weight }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
const id = useRoute().params.id
const { data } = await useFetch(`https://pokeapi.co/api/v2/pokemon/${id}/`)
if (!data.value) {
  throw createError({ statusCode: 404, statusMessage: "Pokemon Not Found" })
}
console.log(data.value)
</script>
