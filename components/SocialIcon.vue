<template>
  <a :href="socialInfo.link" target="_blank" rel="noreferrer">
    <img class="img" :src="image" :alt="socialInfo.label" :aria-label="`${socialInfo.label} logo`" />
  </a>
</template>

<script>
export default {
  props: ['socialInfo'],
  data() {
    return {
      image: require(`../assets/imgs/${this.socialInfo.img}`)
    }
  }
}
</script>

<style lang="scss" scoped>
.img {
      height: 50px;
      width: 50px;
      border-radius: 0;
      &:hover {
        filter: opacity(50%);
      }
    }
</style>