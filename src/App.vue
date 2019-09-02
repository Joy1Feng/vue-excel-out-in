<template>
  <div id="app">
    <ExcelOut/>
    <ExcelIn/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ExcelOut from './components/ExcelOut'
import ExcelIn from './components/ExcelIn'

export default {
  name: 'app',
  components: {
    HelloWorld,
    ExcelOut,
    ExcelIn
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
