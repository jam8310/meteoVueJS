<template>
  <div id="app">
    <meteo />
  </div>
</template>

<script>
import Meteo from './components/meteo'

export default {
  name: 'App',
  components: {
    'meteo' : Meteo
  }
}
</script>

<style>
body{
  padding:5px;
  min-height:100vh;
  background: rgb(2,0,36);
  background: linear-gradient(to bottom, rgba(2,0,36,1) 0%, rgba(238,251,5,1) 0%, rgba(0,212,255,1) 100%);
}
* {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
  }
  

#app {
  font-family: Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  max-width:320px;
  margin:0 auto;
}
</style>
