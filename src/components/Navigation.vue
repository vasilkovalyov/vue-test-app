<template>
  <ul class="navigation">
    <li class="navigation__item" v-for="(item, index) in items" :key="index">
      <router-link :to="item.path" class="navigation__link text-uppercase">{{
        item.name
      }}</router-link>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      defaults: [],
      require: false
    }
  }
}
</script>

<style lang="scss">
@import "@/scss/variables.scss";
@import "@/scss/shared.scss";
.navigation {
  @media (min-width: $media-desktop) {
    display: flex;
    align-items: center;
  }
  &__link {
    color: $white;
    text-decoration: none;

    &:hover {
      opacity: 0.6;
      transition: opacity $speed-animation ease-in-out;
    }
  }
}
</style>
