<template>
  <div class="tac">
    <h1>About Page!</h1>
    <h2>ipSite: {{ ip }}</h2>
    <nuxt-link to="/">
      Home Page
    </nuxt-link>
  </div>
</template>
<script>
export default {
  async asyncData({ $axios, req, res }) {
    const ip = await $axios.$get('http://icanhazip.com')
    return { ip }
  }
}
</script>
<style lang="scss" scoped>
.tac {
  text-align: center;
}
</style>
