<template>
  <span>
    <img src="~/assets/imgs/time.svg" alt />
    <p>{{timeInfo.time}}</p>
  </span>
</template>

<script>
export default {
  props: ['timeInfo']
}
</script>

<style lang="scss" scoped>

span {
    display: flex;
}
</style>