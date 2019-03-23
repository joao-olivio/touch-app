<template>
  <div id="app">
    <Slider />
  </div>
</template>

<script>
import Slider from './components/Slider.vue'

export default {
  name: 'app',
  components: {
    Slider
  }
}
</script>

<style>
* {
  background-position: center center;
  background-repeat: no-repeat;
  background-size: auto 100%;
}

body {
  background-color: black;
  font-family: sans-serif;
  margin: 0;
  padding: 0;
}
</style>
