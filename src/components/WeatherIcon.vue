<template>
  <div>
    <img class="weatherIconBg" height="200" :src="image" alt="" srcset="" />
  </div>

  <!-- <div v-if="weather_description == 'few clouds'">
    <img height="200" src="../assets/weather-icons/02d.svg" alt="" srcset="" />
  </div>

  <div v-else-if="weather_description == 'scattered clouds'">
    <img height="200" src="../assets/weather-icons/03d.svg" alt="" srcset="" />
  </div>

  <div v-else-if="weather_description == 'broken clouds'">
    <img height="200" src="../assets/weather-icons/04d.svg" alt="" srcset="" />
  </div>

  <div v-else-if="weather_description == 'shower rain'">
    <img height="200" src="../assets/weather-icons/09d.svg" alt="" srcset="" />
  </div>

  <div v-else-if="weather_description == 'rain'">
    <img height="200" src="../assets/weather-icons/10d.svg" alt="" srcset="" />
  </div>

  <div v-else-if="weather_description == 'thunderstorm'">
    <img height="200" src="../assets/weather-icons/11d.svg" alt="" srcset="" />
  </div>

  <div v-else-if="weather_description == 'snow'">
    <img height="200" src="../assets/weather-icons/13d.svg" alt="" srcset="" />
  </div>

  <div v-else-if="weather_description == 'mist'">
    <img height="200" src="../assets/weather-icons/50d.svg" alt="" srcset="" />
  </div>

  <div v-else-if="weather_description == 'light rain'">
    <img
      height="200"
      src="../assets/weather-icons/drizzle.svg"
      alt=""
      srcset=""
    />
  </div>

  <div v-else-if="weather_description == 'overcast clouds' || weather_description == 'broken clouds'">
    <img height="200" src="../assets/weather-icons/overcast.svg" alt="" srcset="" />
  </div> -->
</template>

<script>
export default {
  props: ["weatherIconCode"],
  data() {
    return {
      image: require("../assets/weather-icons/" +
        this.weatherIconCode +
        ".svg"),
    };
  },
  methods: {
    updateIcon() {
      this.image = require("../assets/weather-icons/" +
        this.weatherIconCode +
        ".svg");
    },
  },
  updated() {
    this.updateIcon();
  },
  // methods: {
  //     checkIcon() {

  //     }
  // },
  // mounted() {
  //     this.checkIcon()
  //     //console.log(this.weatherIconCode)
  // }
};
</script>

<style>
.weatherIconBg {
  display: inline-block;
  padding: 10px 25px;

  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(0, 255, 255, 0.25);
  border-radius: 16px;
  margin-bottom: 30px;
}
</style>