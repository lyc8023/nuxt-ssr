<template>
  <div class="tac">
    <h1>{{ name }} Page!</h1>
    <h2>ipSite: {{ ip }}</h2>
    <ul>
      <li v-for="(item, index) in list" :key="index">
        name{{ index }} : {{ item }}
      </li>
    </ul>
    <ol>
      <li v-for="(item, index) in info" :key="index">
        <span>{{ item.userName }}</span>
        <span>{{ item.age }}</span>
      </li>
    </ol>
    <nuxt-link to="/">
      Home Page
    </nuxt-link>
  </div>
</template>
<script>
import { mapState } from 'vuex'
export default {
  data() {
    return {
      info: []
    }
  },
  computed: {
    ...mapState('about', ['name', 'list'])
  },
  async asyncData({ $axios, req, res }) {
    const ip = await $axios.$get('http://icanhazip.com')
    return { ip }
  },
  async created() {
    const info = await this.$axios.$get('/koa-api/users/info')
    this.info = info.result
  }
}
</script>
<style lang="scss" scoped>
.tac {
  text-align: center;
}
</style>
