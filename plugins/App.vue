<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo2.png" width="500" />
    <HelloWorld msg="Welcome to Your Vue.js App" />

    <Anime />
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'//
import Anime from "./components/Anime.vue";
export default {
  name: "App",
  components: {
    //HelloWorld//
    Anime,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #50659e;
  height: 1000px;
}
</style>
