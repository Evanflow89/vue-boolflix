<template>
  <div class="container">
    <h2>Movies</h2>
    <ul class="d-flex justify-content-center">
      <li v-for="film in data.films" :key="film.id" class="col-xl-2">
        <div class="card">
          <div class="cover">
            <img :src="imgPath(film.poster_path)" :alt="film.title" />
          </div>
          <div class="content_card">
            <span>Titolo del Film : {{ film.title }}</span>
            <span>Titolo Originale : {{ film.original_title }}</span>
            <span
              >Lingua :
              <country-flag
                :country="flag(film.original_language)"
                size="small"
            /></span>
            <span class="stars" v-html="stars(film.vote_average)"></span>
          </div>
        </div>
      </li>
    </ul>

    <section class="Series">
      <div class="row">
        <div class="col-12 text-center">
          <h2>Series</h2>
          <ul>
            <li v-for="serie in data.series" :key="serie.id">
              <img :src="imgPath(serie.poster_path)" :alt="serie.name" />
              <span>Titolo della Serie : {{ serie.name }}</span>
              <span>Titolo Originale : {{ serie.original_name }}</span>
              <span
                >Lingua :
                <country-flag
                  :country="flag(serie.original_language)"
                  size="small"
              /></span>
              <span class="stars" v-html="stars(serie.vote_average)"></span>
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
ul {
  list-style: none;
  gap: 1.25rem;
  flex-wrap: wrap;
}

ul li {
  display: flex;
  align-items: center;
}

li span {
  font-weight: 600;
}

li img {
  width: 100%;
}

.content_card {
  background-color: black;
  color: white;
  display: none;
  flex-direction: column;
  flex-wrap: wrap;
  width: 100%;
  height: 100%;
}

ul li:hover {
  .content_card {
    display: flex;
  }
  .cover {
    display: none;
  }
}

.stars {
  color: #f1c800;
}
</style>