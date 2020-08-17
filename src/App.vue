<template>
  <div id="app">
    <QrGenerator />
  </div>
</template>

<script>
import QrGenerator from "./components/QrGenerator.vue";

export default {
  name: "App",
  components: {
    QrGenerator,
  },
};
</script>

<style>
body {
  background: #be93c5; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to right,
    #7bc6cc,
    #be93c5
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to right,
    #7bc6cc,
    #be93c5
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
