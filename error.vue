<template>
  <div class="flex items-center justify-center h-screen flex-col">
    <p class="text-5xl text-gray-400 font-bold">{{ error.statusCode }}</p>
    <p class="text-gray-300 text-sm font-thin mt-2">
      {{ error.statusMessage }}
    </p>

    <button
      class="w-[100px] rounded-full text-xs bg-neutral-700 text-neutral-100 p-2 mt-5"
      @click="handleBack"
    >
      Back to home
    </button>
  </div>
</template>

<script setup>
defineProps(["error"])
const handleBack = () => {
  clearError({ redirect: "/" })
}
</script>
