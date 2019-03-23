<template>
    <div class='slider-panel' :style="stylez"></div>
</template>

<script>
export default {
    name: 'SliderItem',
    props: ['stylez'],
    mounted () {
        
    }
}
</script>

<style>
.slider-panel {
  padding-top: 10%;
  width: 100%;
}


</style>
