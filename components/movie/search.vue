<script lang="ts" setup>
const query = ref("")
const movies = ref([])

async function search() {
  const { Search } = await $fetch(`http://omdbapi.com?apikey=a2e42636&s=${query.value}`)
  movies.value = Search
}
</script>

<template>
  <form @submit.prevent="search">
    <input type="text" v-model="query" />
     <button>Search</button>
  </form>
  <ul style="display: flex; flex-wrap: wrap; gap: 10px; list-style: none">
    <li v-for="movie in movies" :key="movie.imdbID">
      <NuxtLink :to="{ name: 'movies-id', params: { id: movie.imdbID } }">
        <img :src="movie.Poster" :alt="movie.title" width="100" />
      </NuxtLink>
    </li>
  </ul>
</template>

<style scoped></style>
