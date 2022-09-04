<script>
  import { slotFlagsText } from "@vue/shared";
import axios from "axios";
  export default {
    data: function () {
      return {
        message: "Welcome to Vue.js!",
        newMovie:{},
        movies: []
      };
    },
    created: function () {},
    methods: {
      movieCreate(){
        console.log("creating a new movie...")
        console.log(this.newMovie)
        axios.post("http://localhost:3000/movies.json", this.newMovie).then(response => {
          console.log(response.data)
      this.movies.push(response.data)
     })

      }
    },
  };
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div>
      Name: <input type="text" v-model="newMovie.name">
      Year: <input type="text" v-model="newMovie.year">
      <button v-on:click="movieCreate()"> Sumbit</button>
    </div>
  </div>
</template>

<style>
</style>