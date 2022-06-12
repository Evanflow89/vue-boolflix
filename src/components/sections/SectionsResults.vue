<template>
  <div class="container-fluid">
    <section class="Movies">
      <div class="row">
        <card-net />
      </div>
    </section>
  </div>
</template>

<script>
import CardNet from "../commons/CardNet.vue";
import search from "../../shared/search.js";
import data from "../../shared/data.js";

export default {
  name: "SectionsResults",
  components: { CardNet },
  data() {
    return {
      search,
      data,
    };
  },
};
</script>

<style lang="scss">
</style>