<template>
  <div id="app">
    <MerchantList/>
  </div>
</template>

<script>
import MerchantList from './components/merchantlist/Page.vue'

export default {
  name: 'app',
  components: {
    MerchantList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
