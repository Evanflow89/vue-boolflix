<template>
  <header>
    <div class="logo">
      <img src="../../assets/img/NetflixLogo.png" alt="Netflix Logo" />
    </div>
    <div class="searchbar">
      <search-bar />
    </div>
  </header>
</template>

<script>
import SearchBar from "../commons/SearchBar.vue";
export default {
  components: { SearchBar },
};
</script>

<style lang="scss">
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: black;

  .logo img {
    padding: 0.625rem;
    max-width: 9.375rem;
  }
}
</style>