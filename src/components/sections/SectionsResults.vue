<template>
  <div class="container">
    <div class="row">
      <div class="col-12 text-center">
        <ul>
          <li v-for="film in films" :key="film.id">
            <span>Titolo del Film : {{ film.title }}</span>
            <span>Titolo Originale : {{ film.original_title }}</span>
            <span>Lingua : {{ film.original_language }}</span>
            <span>Voto Medio :{{ film.vote_average }}</span>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import search from "../../shared/search.js";

export default {
  name: "SectionsResults",
  data() {
    return {
      search,
      films: [],
    };
  },
  created() {
    axios
      .get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "a7f35c47cf7e3c0ea7a66c66aec0b919",
          query: "prova",
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

<style lang="scss">
ul {
  list-style: none;
  padding: 1.25rem;
}
ul li {
  display: flex;
  flex-direction: column;
  padding: 1.25rem;
}
li span {
  font-weight: 600;
}
</style>