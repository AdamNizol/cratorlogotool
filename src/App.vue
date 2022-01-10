<template>
  <div id="app">
    <LogoDisplay msg="Crator Logo"/>
  </div>
</template>

<script>
import LogoDisplay from './components/LogoDisplay.vue'

export default {
  name: 'App',
  components: {
    LogoDisplay
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body{
  background-color: #EEF;
}
</style>
