<template>
  <div class="form">
    <form @submit.prevent="searching">
      <input type="text" v-model="search.search" />
      <button>Submit</button>
    </form>
  </div>
</template>

<script>
import search from "../../shared/search";
import data from "../../shared/data.js";
import axios from "axios";
export default {
  name: "SearchBar",
  data() {
    return {
      search,
      data,
    };
  },
  methods: {
    searching() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "a7f35c47cf7e3c0ea7a66c66aec0b919",
            query: this.search.search,
            language: "it-IT",
          },
        })
        .then((response) => {
          data.films = response.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "a7f35c47cf7e3c0ea7a66c66aec0b919",
            query: this.search.search,
            language: "it-IT",
          },
        })
        .then((response) => {
          data.series = response.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
.form {
  padding-right: 0.625rem;
  display: flex;
}
</style>