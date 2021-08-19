<template>
  <section class="section-products">
    <Loader v-if="loadingProducts" />
    <div class="container">
      <h1>Products page</h1>
      <div class="products-list" v-if="!loadingProducts">
        <div class="col" v-for="item in products" :key="item.id">
          <ProductCard :image="item.image" :title="item.name" :temperament="item.temperament" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import ProductCard from '@/components/ProductCard.vue'
import Loader from '@/components/Loader.vue'
import axios from 'axios'

export default {
  data: () => ({
    products: [],
    loadingProducts: true
  }),
  async mounted () {
    const url = 'https://api.thedogapi.com/v1/breeds'
    try {
      const response = await axios
        .get(url, {
          params: {
            limit: 10,
            page: 0
          }
        })
      this.products = response.data
      this.loadingProducts = false
    } catch (e) {
      this.loadingProducts = false
    }
  },
  components: {
    ProductCard,
    Loader
  }
}
</script>

<style lang="scss">
@import "@/scss/variables.scss";

.section-products {
  position: relative;
  padding: 40px 0;
  min-height: 50vh;

  h1 {
    margin-bottom: 50px;
  }
}

.products-list {
  display: flex;
  flex-wrap: wrap;

  @media (min-width: $media-mobile-md){
    margin: 0 -10px;
  }

  @media (min-width: $media-desktop){
    margin: 0 -25px;
  }
  .col {
    margin-bottom: 25px;

    @media (min-width: $media-mobile-md){
      display: flex;
      width: 50%;
      padding: 0 10px;
    }
    @media (min-width: $media-desktop){
      width: 25%;
      padding: 0 25px;
    }
  }
}
</style>
