<template>
  <div class="about">
    <div class="card">
      <h2>About</h2>
      <h4 style="font-weight: normal; margin-top: 25px; letter-spacing: 1.2px">
        This app returns current weather information about a requested city. It
        was build using Vue.js with OpenWeatherMap API's help
      </h4>
    </div>

    <div class="card card-contact">
      <h3>Contact Me:</h3>

      <div style="margin: 20px 0px;">
        <div title="Mail me" style="margin-bottom: 20px; display:flex; justify-content:space-around; align-items: center">
          <a href="mailto:ali3abbasov@gmail.com">Mail me</a>    <a href="https://github.com/aliabb01">Find me on <img height="25" src="../assets/github-logo.svg" alt="" srcset=""></a>
        </div>
        
        <div title="On GitHub">
          
        </div>

      </div>
      
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.about {
  text-align: center;
}

.card {
  background-color: #42b883;
  border-radius: 15px;
  margin: 50px 15%;
  padding: 20px 15px;
}

.card-contact {
  border-left: 15px solid #35495e;
}
</style>