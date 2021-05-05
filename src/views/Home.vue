<template>
  <div class="home" :class="typeof weather.main != 'undefined' && weather.main.temp > 16 ?
    'warm' : ''">
    <main>


      <div class="search-box">
        <input type="text" 
        class="search-bar" 
        placeholder="Search for a city" 
        v-model="query"
        @keyup="fetchWeather"
        autofocus>
      </div>      

      <div v-if="query && fetchError==true && !loading" class="weather-error" style="color:white">
        No data found for {{ query }}
      </div>

      <div v-if="loading" style="" class="loaderDiv">
        <Loader />
      </div>

      <div class="weather-wrap" v-if="(typeof weather.main != 'undefined') && !loading">
        <div class="location-box">
          <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
          <div class="date">{{ dateBuilder() }}</div>
        </div>

        <div class="weather-box">
          <div style="margin-top: 40px;" class="">
            <div class="weather-icon">
              <WeatherIcon :weatherIconCode="weatherIconCode" />              
            </div>                      
            
            <!-- <img :src="'http://openweathermap.org/img/wn/' + weather.weather[0].icon + '@2x.png'" alt="Something"> -->
          </div>

          <div class="weather">{{ weather.weather[0].main }}</div>

          <div class="temp">{{ Math.round(weather.main.temp) }}°</div>          

          <div style="color:white; margin: 30px 0px;">
            <p style="text-transform: capitalize">{{ weather_description }}</p>
          </div>
          
          <div style="color: white; font-size: 1.2em; margin-top: 1em">
            <p><span style="font-style: italic;">Feels like </span> {{ weather.main.feels_like }}°</p>
          </div>
        </div>     

        
      </div>
    </main>
  </div>
</template>

<script>
import WeatherIcon from '../components/WeatherIcon.vue'
import Loader from 'vue-spinner/src/ScaleLoader'

export default {  
  name: "Home",
  components: { WeatherIcon, Loader },
  data() {
    return {
      api_key: process.env.VUE_APP_OPENWEATHER_API_KEY,
      url_base: "https://api.openweathermap.org/data/2.5/",
      query: '',
      weather: {},
      weather_description: '',
      weatherIconCode: '',
      fetchError: false,
      loading: false,
    };
  },
  methods: {
    fetchWeather() {
        this.loadData()
        const ftch = fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
        .then(res => {
          return res.json();
        }).then(this.setResults)
        .catch((error) => {
          this.catchError()
        })        
    },
    catchError(err) {
      this.fetchError = true
    },
    setResults(results) {
      
      this.weatherIconCode = ''
      this.fetchError = false
      this.weather = results
      this.weather_description = results.weather[0].description
      this.weatherIconCode = results.weather[0].icon
    },
    dateBuilder() {
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July",
      "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday",
      "Saturday"];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();

      return `${day} ${date} ${month} ${year}`;
    },
    loadData() {
      this.loading = true;

      setTimeout(() => {
        this.loading = false
      }, 1000)
    }
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "montserrat", sans-serif;
}

.home {
  background-image: url(".././assets/cold-bg.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

.home.warm {
  background-image: url(".././assets/warm-bg.jpg");
}

main {
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.25),
    rgba(0, 0, 0, 0.75)
  );
}

.search-box {
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 25px;
  transition: 0.4s;
  border: 1px solid transparent;
}

.search-box .search-bar:focus {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border: 1px solid rgb(9, 124, 255);
}

.location-box .location {
  color: #fff;
  font-size: 32px;
  font-weight: 50;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.location-box .date {
  color: #fff;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #fff;
  font-size: 102px;
  font-weight: 900;

  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;

  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.weather-box .weather {
  color: #fff;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  margin-bottom: 30px;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.loaderDiv {
  color: white;
  display: flex;
  justify-content:center;
  align-items: center;
  margin: 0px auto;
}
</style>
