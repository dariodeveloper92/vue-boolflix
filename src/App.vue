<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Header />
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style lang="scss">
  @import "./styles/general.scss";
</style>
