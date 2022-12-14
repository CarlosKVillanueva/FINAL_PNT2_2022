<template>
  <div id="app">
    <ConversorDolaresComp></ConversorDolaresComp>
  </div>
</template>

<script>
import ConversorDolaresComp from './components/ConversorDolaresComp.vue'

export default {
  name: 'App',
  components: {
    ConversorDolaresComp
  }
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
