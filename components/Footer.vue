<template>
  <footer class="footer">
    <div class="footer logo__wrapper">
      <p>This site was built with Nuxt.js and Vue.js</p>
      <p>Hosted on Netlify</p>
      <SocialIcon v-for="icon in footerIcons" :key="icon.label" :socialInfo="icon" />
      <p>© Amy McCabe 2019</p>
      <a href="https://github.com/amyloula/nuxt-vuejs-personal-site">< See-the-source-code-here / ></a>
    </div>
  </footer>
</template>

<script>
import SocialIcon from '~/components/SocialIcon.vue'
export default {
  components: {
    SocialIcon
  },
  data() {
    return {
      footerIcons: [
        {
          link: 'https://nuxtjs.org',
          img: 'nuxtjs.svg',
          label: 'Nuxt.js'
        },
        {
          link: 'https://vuejs.org/',
          img: 'vuejs.svg',
          label: 'Vue.js'
        },
        {
          link: 'http://netlify.com',
          img: 'netlify.svg',
          label: 'Netlify'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~assets/styles/_variables.scss';
.footer {
  height: auto;
  padding: 2rem;
  font-family: $main-body-font;
  .logo__wrapper {
    margin: 0 auto;
    width: 50%;
    text-align: center;
    .img {
      height: 3rem;
      width: 3rem;
    }
  }
}

@media (max-width: 768px) {
  .footer {
    .logo__wrapper {
      width: 100%;
    }
  }
}
</style>