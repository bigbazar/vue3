<template>
  <div :id="`p-${count}`">
<div v-html="demoHtml"></div>    
  Compteur {{ count }}
  </div>
  <div :style="{color:count >= 5 ? 'green' : 'red'}">
  <div :class="{active: true}" v-if="count >= 5">Bravo vous avez incrémenté 5 fois ou plus</div>
  <div :class="{active: false}" v-else="count < 5">Vous avez incrémenté moins de 5 fois</div>
  </div>

  <p>
  <button @click="increment">Incrémenter</button>
  <button @click="decrement">Décrémenter</button>
  </p>

  <hr>

  <form action="" @submit.prevent="addMovie">
    <input type="text" placeholder="Nouveau film" v-model="movieName"> {{ movieName }}
    <button>Ajouter</button>
  </form>

  <p>
    <button @click="sortMovies">Trier les films</button>
  </p>
  
  <ul>
    <li v-for="movie in movies"
    :key="movie">
      {{ movie }} <button @click="deleteMovie(movie)">Supprimer</button>

    </li>
  </ul>

</template>

<script setup>
import {ref} from 'vue'

const count = ref(0)
console.log(count, count.value)
const demoHtml = '<span>Demo</span>'
const movieName = ref('')

const movies = ref([
  'Matrix',
  'Lilo a Stitch',
  'Titanic'
])

const increment = (event) => {
  console.log(event)
  count.value++
}

const decrement = () => {
  count.value--
}

const deleteMovie = (movie) => {
  movies.value = movies.value.filter(m => m != movie)
}

const sortMovies = () => {
  movies.value.sort((a, b) => a > b ? 1 : -1)
}

const addMovie = (event) => {
  movies.value.push(movieName.value)
  movieName.value = ""
}

</script>

<style>
.active {
  background-color: pink;
}
</style>
