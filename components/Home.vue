<template>
  <div class="home">
    <div class="img-container">
      <div class="text-container">
        <h1 class="large-title">
          Amy
          <br />& Ger
        </h1>
        <h1>03-11-19</h1>
        <h3>We're getting married!</h3>
      </div>
    </div>
    <div class="main-body__container">

    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
@import '~assets/styles/_variables.scss';
.home {
    height: 100%;
    width: 100%;
}
.img-container {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: 100%;
  height: auto;
  font-family: $main-header-font;
  color: $complementary-accent-color;
  background-image: url('~assets/imgs/villa-oliviero.jpg');
  background-position: center;
}
.text-container {
  background-color: $secondary-accent-color;
  padding: 0.75rem 4rem;
  font-family: 'Just Me Again Down Here', cursive;
}

.large-title {
  font-size: 4rem;
}
</style>