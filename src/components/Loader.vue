<template>
  <div class="loader"></div>
</template>
<style lang="scss">
  @import "@/scss/variables.scss";
  .loader {
    width: 30px;
    height: 30px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translateX(-50%, -50%);
    border: 3px solid $primary-color;
    border-top-color: transparent;
    border-bottom-color: transparent;
    border-radius: 50%;
    animation: 1s loader linear infinite;
  }

  @keyframes loader {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
