<template>
    <div class='has-slider'>
        <div class='slider' id='slider' v-pan="onPan">
            <SliderItem stylez='background-color: #faaf34; background-image: url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/40288/65d721_4dfa47a05152487fb3bc45ca2ec8fd1e.png)' />
            <SliderItem stylez='background-color: #aca680; background-image: url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/40288/65d721_761db9a0c113407f924a824ed173ed26.png)' />
            <SliderItem stylez='background-color: #d8daa6; background-image: url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/40288/tumblr_njkn6kp0kE1qgsw73o1_500.png)' />
        </div>
    </div>
</template>

<script>
import SliderItem from './SliderItem';

export default {
    name: 'Slider',
    components: {
        SliderItem
    },
    data () {
        return {
            slideCount: 3,
            activeSlide: 0,
            sliderEl: ''
        }
    },
    mounted: function () {
        this.sliderEl = this.$el.querySelector('.slider');
        this.slideCount = this.sliderEl.children.length;
    },
    methods: {
        onPan: function (event) {
            var percentage = 100 / this.slideCount * event.deltaX / window.innerWidth;
            var transformPercentage = percentage - 100 / this.slideCount * this.activeSlide; // NEW
            this.sliderEl.style.transform = 'translateX( ' + transformPercentage + '% )';
            if( event.isFinal ) { // NEW: this only runs on event end
                if( percentage < 0 )
                    this.goToSlide( this.activeSlide + 1 );
                else if( percentage > 0 )
                    this.goToSlide( this.activeSlide - 1 );
                else
                    this.goToSlide( this.activeSlide );
            }
        },
        goToSlide: function (number) {
            if( number < 0 )
                this.activeSlide = 0;
            else if( number > this.slideCount - 1 )
                this.activeSlide = this.slideCount - 1
            else
                this.activeSlide = number;

            var percentage = -( 100 / this.slideCount ) * this.activeSlide;
            this.sliderEl.style.transform = 'translateX( ' + percentage + '% )';
        }
    }
}
</script>

<style>
.slider {
  display: flex;
  transition: -webkit-transform 400ms cubic-bezier(0.5, 0, 0.5, 1);
  transition: transform 400ms cubic-bezier(0.5, 0, 0.5, 1);
  transition: transform 400ms cubic-bezier(0.5, 0, 0.5, 1), -webkit-transform 400ms cubic-bezier(0.5, 0, 0.5, 1);
  width: 300%;
}

.has-slider {
  overflow: hidden;
  width: 100%;
}
.has-slider::after {
  -webkit-animation: flash 1s infinite;
          animation: flash 1s infinite;
  color: red;
  content: "SLUG MODE";
  font: 700 48px/1 sans-serif;
  left: 50%;
  pointer-events: none;
  position: absolute;
  top: 50%;
  -webkit-transform: translate(-50%, -50%);
          transform: translate(-50%, -50%);
}
</style>
