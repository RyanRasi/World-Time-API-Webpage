<template>
  <div id="app">
    <Header />
    <WorldTimeAPI />

    <div class="fixed-bottom">
      <p>
        Uses the World Time API
        <a href="http://worldtimeapi.org/" target="_top">Visit here!</a>
      </p>
      <p>
        Created by Ryan Rasi
        <a href="https://github.com/RyanRasi" target="_top">Github.com!</a>
      </p>
    </div>
  </div>
</template>

<script>
import WorldTimeAPI from "./components/WorldTimeAPI.vue";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    Header,
    WorldTimeAPI
  },
  data() {
    return {};
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
