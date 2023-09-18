<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const moviesGenres = ref([])
const TVGenres = ref([])

onMounted(async () => {
  let response = await axios.get('https://api.themoviedb.org/3/genre/movie/list?language=pt-BR', {
    headers: {
      Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIzY2VlM2ZlOWZiOWVjODBjMGU4ZGMzOTA3ODY5MzRlOSIsInN1YiI6IjY0ZmYxNTdmZTBjYTdmMDBlYzhjNmM3OSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.ym4SgeQgijAp5EPevgnOxRK9UWpnaJhDQ9dPF4SYh3w'
    }
  })
  moviesGenres.value = response.data.genres
  response =  await axios.get('https://api.themoviedb.org/3/genre/tv/list?language=pt-BR', {
    headers: {
      Authorization: `Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIzY2VlM2ZlOWZiOWVjODBjMGU4ZGMzOTA3ODY5MzRlOSIsInN1YiI6IjY0ZmYxNTdmZTBjYTdmMDBlYzhjNmM3OSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.ym4SgeQgijAp5EPevgnOxRK9UWpnaJhDQ9dPF4SYh3w`
    }
  })
  TVGenres.value = response.data.genres
})
</script>

<template>
  <div class="generos">
    <h1>Gêneros de filmes</h1>
    <ul>
      <li v-for="genre in moviesGenres" :key="genre.id">
        
      </li>
    </ul>
    <hr />
    <h1>Gêneros de programas de TV</h1>
    <ul>
      <li v-for="genre in TVGenres" :key="genre.id">
        
      </li>
    </ul>
  </div>
  </template>

<style scoped>

.generos {
  color: wheat;
}

</style>