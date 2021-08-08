<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <ListOfCities/>
</template>

<script>
import ListOfCities from './components/ListOfCities.vue'
import "bootstrap/dist/css/bootstrap.min.css"


export default {
  name: 'App',
  components: {
    ListOfCities
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
  margin-top: 60px;
}
</style>
