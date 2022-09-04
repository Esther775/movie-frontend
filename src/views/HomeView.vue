

<script>
import axios from "axios"

  export default {
    data: function () {
      return {
        message: "Movie Home Page!",
        movies: []
      };
    },
    created: function () {
     this.moviesIndex()
    },
    methods: {
      moviesIndex(){
        console.log("showing all movies");
        axios.get("http://localhost:3000/movies").then(response => {
          console.log(response.data)
          this.movies = response.data
        })
      }

    },
  };
</script>

<template>



  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="movie in movies">
      <p> Name of Movie: {{movie.name}} </p>
      <hr />

    </div>

  </div>
</template>

<style>
</style>
