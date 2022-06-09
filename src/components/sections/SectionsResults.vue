<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <ul>
          <li v-for="film in films" :key="film.id">{{ film.title }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SectionsResults",
  data() {
    return {
      films: [],
    };
  },
  created() {
    axios
      .get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "a7f35c47cf7e3c0ea7a66c66aec0b919",
          query: "ritorno",
          language: "it-IT",
        },
      })
      .then((response) => {
        this.films = response.data.results;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style>
</style>