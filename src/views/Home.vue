<template>
  <section class='section-home'>
    <div class='container'>
      <h1>Home page</h1>
      <Loader v-if='loadingProducts' />
      <Carousel v-if='!loadingProducts' :items='products' />
    </div>
  </section>
</template>

<script>
import Carousel from '@/components/Carousel.vue'
import Loader from '@/components/Loader.vue'

import axios from 'axios'

export default {
  data: () => ({
    products: [],
    loadingProducts: true
  }),
  async mounted () {
    console.log(this.$root.globalVar)
    const url = 'https://api.thedogapi.com/v1/breeds'
    try {
      const response = await axios.get(url, {
        params: {
          limit: 8,
          page: 1
        }
      })
      this.products = response.data
      this.loadingProducts = false
    } catch (e) {
      console.log(e)
      this.loadingProducts = false
    }
  },
  components: {
    Carousel,
    Loader
  }
}
</script>

<style lang='scss'>
.section-home {
  padding: 40px 0;
  position: relative;
  min-height: 50vh;

  h1 {
    margin-bottom: 50px;
  }
}
</style>
