<template>
  <div>
    <img class="weatherIconBg" height="200" :src="image" alt="" srcset="" />
  </div>
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
};
</script>

<style>
.weatherIconBg {
  display: inline-block;
  padding: 10px 25px;

  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(0, 0, 0, 0.20);
  border-radius: 16px;
  margin-bottom: 30px;
}
</style>