<script setup>
// import { NuxtLink } from "#build/components";

const query = ref("");
const movies = ref([]);
const search = async () => {
  const { Search } = await $fetch(
    `http://www.omdbapi.com/?apikey=d604b2dc&s=${query.value}`
  );
  console.log("data : ", Search);
  movies.value = Search;
};
</script>

<template>
  <div>
    <form @submit.prevent="search()">
      <input type="text" v-model="query" />
      <button>Search</button>
    </form>
    <ul style="display: flex; flex-wrap: wrap; gap: 10px; list-style: none">
      <li v-for="movie in movies" :key="movie.imdbID">
        <NuxtLink :to="{ name: 'movies-id', params: { id: movie.imdbID } }">
          <img :src="movie.Poster" :alt="movie.title" />
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
