<template>
  <div class='carousel'>
    <VueSlickCarousel v-bind=settings>
      <div class="slide-item" v-for='item in items' :key='item.id'>
        <ProductCard :image='item.image' :title='item.name' />
      </div>
      <template #prevArrow>
          <div class="prevArrow">
            <img src=../assets/arrow-left.svg alt=prev arrow>
          </div>
      </template>
      <template #nextArrow>
          <div class="nextArrow">
            <img src=../assets/arrow-right.svg alt=next arrow>
          </div>
      </template>
    </VueSlickCarousel>
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue'
import VueSlickCarousel from 'vue-slick-carousel'
import 'swiper/swiper.scss'

export default {
  props: {
    items: {
      type: Array,
      require: false,
      defaults: []
    }
  },
  data: () => ({
    settings: {
      arrows: true,
      centerPadding: '50px',
      responsive: [
        {
          breakpoint: 2560,
          settings: {
            slidesToShow: 3,
            slidesToScroll: 1,
            infinite: false
          }
        },
        {
          breakpoint: 1024,
          settings: {
            slidesToShow: 2,
            slidesToScroll: 1,
            infinite: false
          }
        },
        {
          breakpoint: 480,
          settings: {
            slidesToShow: 1,
            slidesToScroll: 1,
            infinite: false
          }
        }
      ]
    }
  }),
  components: {
    VueSlickCarousel,
    ProductCard
  }
}
</script>

<style lang='scss'>
@import '@/scss/variables.scss';

.carousel {
  overflow: hidden;
  margin: 0 -50px;
}

.slick-slider {
  position: relative;
  padding: 0 30px;
}

.slick-track {
  display: flex;
}

.slick-list {
  overflow: hidden;

  @media (max-width: $media-tablet) {
    padding-bottom: 79px;
  }
}

.slide-item {
  padding: 0 20px;
}

.slick-arrow {
  color: $black;
  width: 40px;
  height: 40px;
  position: absolute;
  z-index: 10;
  bottom: 15px;
  border: 1px solid $gray;
  box-shadow: 1px 1px 5px 0px rgba($black,0.75);
  border-radius: 50%;
  background-color: $white;
  transition: transform 0.3s ease-in-out;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;

  @media (min-width: $media-tablet) {
    top: 50%;
    bottom: auto;
  }

  &:hover {
    transform: scale(1.2);
  }

  &:after {
    color: inherit;
  }

  &.slick-next {
    right: 100px;

    @media (min-width: $media-tablet) {
      right: 38px;
    }

    @media (min-width: $media-desktop) {
      right: 30px;
    }
  }

  &.slick-prev {
    left: 100px;

    @media (min-width: $media-tablet) {
      left: 38px;
    }

    @media (min-width: $media-desktop) {
      left: 30px;
    }
  }

  &.slick-disabled {
    display: none;
  }

  img {
    width: 20px;
  }
}

</style>
