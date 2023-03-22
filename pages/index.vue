<template>
  <main>
    <h1 class="text-2xl text-neutral-100 font-bold">Pokemon list</h1>
    <!-- SEARCH -->
    

    <!-- POKEMONLIST -->

    <div
      class="grid grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-6 mt-5 gap-4"
    >
      <PokeCard
        v-for="pokemon in pokemons"
        :pokemon="pokemon"
        :key="pokemon.id"
      />
    </div>
  </main>
</template>
<script setup>
const { data } = await useFetch("https://pokeapi.co/api/v2/pokemon")

const pokemons = await Promise.all(
  data.value.results.map(async (poke) => {
    const { data: pokeData } = await useFetch(poke.url)

    return {
      id: pokeData.value.id,
      name: pokeData.value.name,
      image: pokeData.value.sprites.front_default,
    }
  })
)

// definePageMeta({
//   layout: "another",
// })
</script>
