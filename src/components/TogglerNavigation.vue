<template>
  <div :class="['hamburger hamburger--squeeze', className, isOpen ? 'nav-active' : '']" @click="onClick" >
    <span class="hamburger-box">
      <span class="hamburger-inner"></span>
    </span>
  </div>
</template>
<script>
export default {
  props: {
    className: {
      type: String,
      defaults: null,
      require: false
    },
    isOpen: {
      type: Boolean,
      defaults: false,
      require: false
    }
  },
  methods: {
    onClick () {
      this.$emit('handleClick')
    }
  }
}
</script>
<style lang="scss">
@import "@/scss/variables.scss";

.hamburger {
  display: flex;
  align-items: center;
  text-decoration: none;
  cursor: pointer;
  transition-property: opacity, filter;
  transition-duration: 0.15s;
  transition-timing-function: linear;
  font: inherit;
  color: inherit;
  text-transform: none;
  background-color: transparent;
  border: 0;
  margin: 0;
  overflow: visible;
  position: relative;
  z-index: 1;

  &.nav-active {
      .hamburger-inner {
        transform: rotate(45deg);
        transition-delay: 0.12s;
        transition-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
        &::before {
          top: 0;
          opacity: 0;
          transition: top 0.075s ease, opacity 0.075s 0.12s ease;
        }
        &::after {
          bottom: 0;
          transform: rotate(-90deg);
          transition: bottom 0.075s ease,
            transform 0.075s 0.12s cubic-bezier(0.215, 0.61, 0.355, 1);
        }
      }
    }
}

.hamburger-box {
  width: 30px;
  height: 30px;
  display: inline-block;
  position: relative;
  min-width: 14px;
}

.hamburger-inner {
  display: block;
  top: 50%;
  width: 100%;
  margin-top: 30px / -2;
  &,
  &::before,
  &::after {
    width: 30px;
    height: 2px;
    background-color: $white;
    border-radius: 2px;
    position: absolute;
    transition-property: transform;
    transition-duration: 0.15s;
    transition-timing-function: ease;
  }
  &::before,
  &::after {
    content: "";
    display: block;
  }
  &::before {
    top: -8px;
  }
  &::after {
    bottom: -8px;
  }
}

@if index(squeeze, squeeze) {
  /*
     * Squeeze
     */
  .hamburger--squeeze {
    .hamburger-inner {
      transition-duration: 0.075s;
      transition-timing-function: cubic-bezier(0.55, 0.055, 0.675, 0.19);
      &::before {
        transition: top 0.075s 0.12s ease, opacity 0.075s ease;
      }
      &::after {
        transition: bottom 0.075s 0.12s ease,
          transform 0.075s cubic-bezier(0.55, 0.055, 0.675, 0.19);
      }
    }
  }
}

</style>
