<template>
  <div class="card">
    <div class="card__image" v-if="image">
      <img :src="image.url" :alt="title" />
    </div>
    <div class="card__body">
      <h3 class="card__heading" v-if="title">{{ title }}</h3>
      <p v-if="temperament">{{temperament}}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    image: {
      type: Object,
      default: null,
      require: false
    },
    title: {
      type: String,
      default: '',
      require: false
    },
    temperament: {
      type: String,
      default: '',
      require: false
    }
  },
  data: () => ({})
}
</script>
<style lang="scss">
@import "@/scss/variables.scss";

.card {
  border: 1px solid $gray;
  width: 100%;
  &__image {
    width: 100%;
    height: 80vw;
    padding: 20px;
    @media (min-width: $media-mobile-md){
      height: 46vw;
    }
    @media (min-width: $media-desktop){
      height: 20vw;
      max-height: 230px;
    }

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
  &__body {
    padding: 20px;
  }
}
</style>
