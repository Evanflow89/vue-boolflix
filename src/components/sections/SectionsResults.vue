<template>
  <div class="container">
    <section class="Movies">
      <div class="row">
        <div class="col-12 text-center">
          <h2>Movies</h2>
          <ul>
            <li v-for="film in data.films" :key="film.id">
              <span>Titolo del Film : {{ film.title }}</span>
              <span>Titolo Originale : {{ film.original_title }}</span>
              <span>Lingua : {{ film.original_language }}</span>
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
              <span>Lingua : {{ serie.original_language }}</span>
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

export default {
  name: "SectionsResults",
  data() {
    return {
      search,
      data,
    };
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