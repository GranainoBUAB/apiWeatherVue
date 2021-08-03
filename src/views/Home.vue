<template>
  <div class="home">
    <h1>El Tiempo en {{ weather.location.name }}</h1>
    <img
      :src="weather.current.condition.icon"
      style="width: 200px;height:auto;"
    />
    <h2>Temperatura : {{ weather.current.temp_c }} ºC</h2>
    <h2>Humedad : {{ weather.current.humidity }} %</h2>
    <h2>Viento : {{ weather.current.wind_kph }} km/h</h2>
    <h2>Presión : {{ weather.current.pressure_mb }} hpa</h2>
    <h2>Precipitacion : {{ weather.current.precip_mm }} mm</h2>
  </div>
</template>

<script>
import axios from "axios";

const options = {
  method: "GET",
  url: "https://weatherapi-com.p.rapidapi.com/current.json",
  params: { q: "santa fe Andalucia spain" },
  headers: {
    "x-rapidapi-key": "6001a4e8b3mshe0baf1d16d76c04p1082d4jsn4c69a8766f93",
    "x-rapidapi-host": "weatherapi-com.p.rapidapi.com",
  },
};

export default {
  name: "Home",
  components: {},
  data() {
    return {
      weather: [],
    };
  },
  created() {
    this.getWeather();
  },
  methods: {
    async getWeather() {
      const response = await axios.request(options);
      this.weather = response.data;
      console.log(this.weather);
    },
  },
};
</script>
