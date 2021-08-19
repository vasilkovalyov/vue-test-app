<template>
  <div id="app">
    <MainLayout />
  </div>
</template>

<script>

import MainLayout from '@/layouts/MainLayout'

export default {
  data: () => ({}),
  components: {
    MainLayout
  }
}
</script>

<style lang="scss">
  #app {
    width: 100%;
    display: flex;
  }
</style>
