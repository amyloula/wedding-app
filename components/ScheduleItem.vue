<template>
  <div class="schedule__item" :id=scheduleInfo.date>
    <h1>{{scheduleInfo.time}}</h1>
    <h3>{{scheduleInfo.title}}</h3>
    <p>{{scheduleInfo.description}}</p>
    <div class="location__wrapper">
      <img src="~/assets/imgs/location.svg" alt class="src" />
      <p>{{scheduleInfo.location}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['scheduleInfo']
}
</script>
<style lang="scss" scoped>
@import '~assets/styles/_variables.scss';
.schedule__item {
  font-family: $secondary-header-font;
  background-color: $secondary-accent-color;
  border-top: 1px solid $complementary-accent-color;
  margin: 1rem;
  text-align: center;
  h1 {
      
  }
  p {
    font-family: $main-header-font;
  }
  .location__wrapper {
    display: flex;
    justify-content: center;
    p {
      font-family: $secondary-header-font;
    }
  }
}
</style>