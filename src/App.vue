<template>
  <div id="app">
    <bilan/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Bilan from './components/Bilan.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Bilan
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
  margin-top: 60px;
}
</style>
