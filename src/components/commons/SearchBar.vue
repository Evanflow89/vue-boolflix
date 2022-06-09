<template>
  <div class="form">
    <form>
      <input type="text" />
      <button>Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      search,
    };
  },
};
</script>

<style lang="scss">
.form {
  padding-right: 0.625rem;
  display: flex;
}
</style>