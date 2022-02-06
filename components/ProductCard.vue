<template>
  <div>
    <button @click="$fetch">Refresh</button>
    <p v-if="$fetchState.pending">Fetching mountains...</p>
    <p v-else-if="$fetchState.error">An error occurred :(</p>
    <div
      class="md:flex mb-4"
      v-for="mountain in mountains"
      v-else
      :key="mountain.title"
    >
      <div class="md:flex-shrink-0">
        <img
          :src="mountain.image"
          class="rounded-lg md:w-56"
          :alt="mountain.title"
        />
      </div>
      <div class="mt-4 md:mt-0 md:ml-6">
        <div class="uppercase tracking-wide text-sm text-indigo-600 font-bold">
          {{ mountain.continent }}
        </div>
        <NuxtLink
          :to="mountain.slug"
          class="
            block
            mt-1
            text-lg
            leading-tight
            font-semibold
            text-gray-900
            hover:underline
          "
        >
          {{ mountain.title }}
        </NuxtLink>
        <p class="mt-2 text-gray-600">
          {{ mountain.description }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mountains: [],
    }
  },
  async fetch() {
    this.mountains = await fetch('https://api.nuxtjs.dev/mountains').then(
      (res) => res.json()
    )
  },
}
</script>