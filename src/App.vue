<template>
  <div id="app">
    <base-header />
    <base-main />
  </div>
</template>

<script>
import BaseHeader from "./components/blocks/BaseHeader.vue";
import BaseMain from "./components/blocks/BaseMain.vue";
export default {
  name: "App",
  components: {
    BaseHeader,
    BaseMain,
  },
};
</script>

<style lang="scss">
@import "assets/style/global.scss";
</style>
