<template>
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
  <router-view/>
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
  -webkit-box-shadow: 0px 1px 31px 1px rgba(0,0,0,0.16);
-moz-box-shadow: 0px 1px 31px 1px rgba(0,0,0,0.16);
box-shadow: 0px 1px 31px 1px rgba(0,0,0,0.16);
}

.nav-link {
  background: #35495e;
  border-radius: 5px;
  color: white;
  padding: 15px;
  text-decoration: none;
}

.nav-link:hover {
  background-color: #42b883;
}


</style>
