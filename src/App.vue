<template>
  <router-view/>
  <div id="nav">
    <div>
      <h3>vue-weather</h3>
    </div>
    <div cla>
      <router-link class="nav-link" :to="{ name: 'Home' }">Home</router-link>
    </div>
    <div>
      <router-link class="nav-link" :to="{ name: 'About' }">About</router-link>
    </div>
  </div>

      <div class="card card-contact">
      <h3>Contact Me:</h3>

      <div style="margin: 20px 0px;">
        <div class="contact-links" style="margin-bottom: 20px; display:flex; justify-content:space-around; align-items: center">
          <a title="Mail me" href="mailto:ali3abbasov@gmail.com">Mail me</a>    <a title="GitHub" href="https://github.com/aliabb01">GitHub</a>
        </div>
      </div>
      
    </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montserrat', sans-serif;
}

#nav {
  display: flex;
  justify-content: space-around;
  padding: 40px 0px;
  border-top: 1px solid black;
}

.nav-link {
  color: #35495e;
  text-decoration: none;
}

.nav-link:hover {
  color: #42b883;
}

.card {
  background-color: #42b883;
  border-radius: 15px;
  margin: 50px 15%;
  padding: 20px 15px;
}

.card-contact {
  border-right: 15px solid #35495e;
}

.contact-links a {
  text-decoration: none;
  color: black;
}

.contact-links a:hover {
  color: #35495e;
}

</style>
