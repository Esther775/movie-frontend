

<script>
import axios from "axios"

  export default {
    data: function () {
      return {
        message: "Movie Home Page!",
        movies: [],
        currentMovie: {}

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
      },
      moviesShow(movieeee){
        console.log("showing specific movie")
        this.currentMovie = movieeee
        document.querySelector('#movie-details').showModal();
      }

    },
  };
</script>

<template>



  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="movie in movies">
      <p> Name of Movie: {{movie.name}} </p>

      <button v-on:click="moviesShow(movie)"> Show More Details</button>
      <hr />
    </div>
    <dialog id="movie-details">
      <form method="dialog">
        <p> Year{{currentMovie.year}}</p>
        <button> Close</button>
      </form>
    </dialog>

  </div>
</template>

<style>
</style>
