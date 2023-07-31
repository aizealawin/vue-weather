<template>
  <div id="app">Hello</div>
</template>

<script>
import axios from 'axios'
const API_KEY = process.env.VUE_APP_WEATHER_KEY

export default {
  name: 'App',
  components: {
  },
  data: () => ({
    dailyWeather: [],
    currentWeather: null
  }),
  methods: {
    async getCurrentWeather(coords) {
      const res = await axios.get(
        `
        https://api.openweathermap.org/data/2.5/onecall?lat=${coords.latitude}&lon=${coords.longitude}&units=imperial&appid=${API_KEY}
        `
      )
      console.log(res.data)
      this.currentWeather = res.data.current
    }
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
