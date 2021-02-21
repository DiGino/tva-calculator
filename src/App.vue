<template>
  <div id="app">
    <Tva msg="Calculez la TVA"/>
  </div>
</template>

<script>
import Tva from './components/Tva.vue'

export default {
  name: 'App',
  components: {
    Tva
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  max-width: 1200px;
  padding: 5em;
}
</style>
