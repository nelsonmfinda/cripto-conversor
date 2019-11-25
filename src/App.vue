<template>
  <div id="app">
    <Navbar />
    <Conversor />
  </div>
</template>

<script>
import Conversor from "./components/Conversor.vue";
import Navbar from "./components/Navbar.vue";

export default {
  name: "app",
  components: {
    Conversor,
    Navbar
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
}
</style>
