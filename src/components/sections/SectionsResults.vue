<template>
  <div class="container">
    <section class="Movies">
      <div class="row">
        <div class="col-12 text-center">
          <h2>Movies</h2>
          <ul>
            <li v-for="film in data.films" :key="film.id">
              <img :src="imgPath(film.poster_path)" alt="" />
              <span>Titolo del Film : {{ film.title }}</span>
              <span>Titolo Originale : {{ film.original_title }}</span>
              <span
                >Lingua :
                <country-flag
                  :country="
                    film.original_language == 'en'
                      ? film.original_language == 'gb'
                      : film.original_language
                  "
                  size="small"
              /></span>
              <span>Voto Medio :{{ film.vote_average }}</span>
            </li>
          </ul>
        </div>
      </div>
    </section>
    <section class="Series">
      <div class="row">
        <div class="col-12 text-center">
          <h2>Series</h2>
          <ul>
            <li v-for="serie in data.series" :key="serie.id">
              <span>Titolo della Serie : {{ serie.name }}</span>
              <span>Titolo Originale : {{ serie.original_name }}</span>
              <span
                >Lingua :
                <country-flag :country="serie.original_language" size="small"
              /></span>
              <span>Voto Medio :{{ serie.vote_average }}</span>
            </li>
          </ul>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import search from "../../shared/search.js";
import data from "../../shared/data.js";
import CountryFlag from "vue-country-flag";

export default {
  name: "SectionsResults",
  components: {
    CountryFlag,
  },
  data() {
    return {
      search,
      data,
    };
  },
  methods: {
    imgPath(url) {
      return `https://image.tmdb.org/t/p/w185/${url}`;
    },
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