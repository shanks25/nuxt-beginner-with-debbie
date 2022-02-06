<template>
  <div class="container m-10">
        <SocialHead
      :title="mountain.title"
      :description="mountain.description"
      :image="mountain.image"
    />
      <NuxtLink to="/products"> back</NuxtLink>
      <h1>{{ mountain.continent }}</h1>
      <img :src="mountain.image" :alt="mountain.title">
    <h1>{{ mountain.title }}</h1>
    <p>{{ mountain.description }}</p>
    <li>Countries - <span v-for="country in mountain.countries" :key="country">
           {{country}} 
        </span> </li>
  </div>
</template>

<script>
  export default {
    async asyncData({ params, $axios }) {
      const mountain = await $axios.$get(`https://api.nuxtjs.dev/mountains/${params.slug}`)
      return { mountain }
    }
  }
</script>