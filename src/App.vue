<template>
  <div id="app">
    <CareerFramework :careerFrameworkData="careerFrameworkData" />
  </div>
</template>

<script>
import careerFrameworkData from "../data.json";
import CareerFramework from "./components/CareerFramework.vue";

export default {
  name: "App",
  components: {
    CareerFramework
  },
  data() {
    return {
      careerFrameworkData
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
