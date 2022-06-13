<template>
  <div class="container">
    <h2 class="text-center">Movies</h2>
    <ul class="d-flex justify-content-center">
      <li
        v-for="film in data.films"
        :key="film.id"
        class="col-12 col-sm-6 col-md-4 col-lg-2 justify-content-center"
      >
        <div class="cover">
          <img :src="imgPath(film.poster_path)" :alt="film.title" />
        </div>
        <div class="content_card">
          <span>Titolo del Film : {{ film.title }}</span>
          <span>Titolo Originale : {{ film.original_title }}</span>
          <span
            >Lingua :
            <country-flag :country="flag(film.original_language)" size="small"
          /></span>
          <span class="stars" v-html="stars(film.vote_average)"></span>
          <span>Overview: {{ film.overview }}</span>
        </div>
      </li>
    </ul>
    <section class="Series">
      <h2 class="text-center">Series</h2>
      <ul class="d-flex justify-content-center">
        <li
          v-for="serie in data.series"
          :key="serie.id"
          class="col-12 col-sm-6 col-md-4 col-lg-2 justify-content-center"
        >
          <div class="cover">
            <img :src="imgPath(serie.poster_path)" :alt="serie.name" />
          </div>
          <div class="content_card">
            <span>Titolo della Serie : {{ serie.name }}</span>
            <span>Titolo Originale : {{ serie.original_name }}</span>
            <span
              >Lingua :
              <country-flag
                :country="flag(serie.original_language)"
                size="small"
            /></span>
            <span class="stars" v-html="stars(serie.vote_average)"></span>
            <span>Overview: {{ serie.overview }}</span>
          </div>
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
import search from "../../shared/search.js";
import data from "../../shared/data.js";
import CountryFlag from "vue-country-flag";

export default {
  name: "CardNet",
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
      if (url === null) {
        return `https://www.clker.com/cliparts/f/Z/G/4/h/Q/no-image-available-md.png`;
      }
      return `https://image.tmdb.org/t/p/w185/${url}`;
    },
    stars(voto) {
      let starFont = "";
      let emptyFont = "";
      let rating = Math.ceil(voto / 2);
      let total = 5;
      for (let i = 0; i < rating; i++) {
        starFont += `<i class="fa-solid fa-star"></i>`;
      }
      for (let i = 0; i < total - rating; i++) {
        emptyFont += `<i class="fa-regular fa-star"></i>`;
      }
      return `${starFont}${emptyFont}`;
    },
    flag(language) {
      if (language === "en") {
        return `gb`;
      } else {
        return language;
      }
    },
  },
};
</script>

<style lang="scss">
h2 {
  padding-bottom: 1.25rem;
  text-transform: uppercase;
  color: white;
}
ul {
  list-style: none;
  flex-wrap: wrap;
  gap: 0.3125rem;
}

ul li {
  display: flex;
  align-items: center;
  margin-bottom: 1.25rem;
  font-size: 0.75rem;
  overflow-y: auto;
}

li span {
  font-weight: 600;
  width: 100%;
}

li img {
  width: 100%;
}

.content_card {
  background-color: black;
  color: white;
  display: none;
  width: 100%;
  height: 100%;
  overflow-y: auto;
}

ul li:hover {
  .content_card {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
  }
  .cover {
    display: none;
  }
}

.stars {
  color: #f1c800;
}
</style>