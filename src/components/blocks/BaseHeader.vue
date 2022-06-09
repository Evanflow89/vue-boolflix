<template>
  <header>
    <div class="logo">
      <img src="../../assets/img/NetflixLogo.png" alt="Netflix Logo" />
    </div>
  </header>
</template>

<script>
export default {};
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