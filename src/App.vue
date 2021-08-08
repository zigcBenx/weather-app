<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <ListOfCities/>
  <WeatherInformation/>
</template>

<script>
import ListOfCities from './components/ListOfCities.vue'
import WeatherInformation from './components/WeatherInformation.vue'
import "bootstrap/dist/css/bootstrap.min.css"


export default {
  name: 'App',
  components: {
    ListOfCities,
    WeatherInformation
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
