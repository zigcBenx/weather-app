<template>
  <div class="wrapper">
    <ListOfCities @updateWeather="updateWeather($event)"/>
    <WeatherInformation :weather="weather"/>
  </div>
</template>

<script>
import ListOfCities from './components/ListOfCities.vue'
import WeatherInformation from './components/WeatherInformation.vue'
import "bootstrap/dist/css/bootstrap.min.css"

export default {
  name: 'App',
  data () {
    return {
      weather: {}
    }
  },
  methods: {
    updateWeather(weather){
      this.weather = weather;
    }
  },
  components: {
    ListOfCities,
    WeatherInformation,
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
