<template>
  <div class="hello" v-pan="onPan">
    
  </div>
</template>

<script>
import Hammer from 'hammerjs';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  created: function () {
    
  },
  methods: {
    onPan: function (event) {
      console.log(event)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  width: 100vw;
  height: 400px;
  background-color: aqua;
}
</style>
