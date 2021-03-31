<template>
  <div class="container">
    <CircleTimer
      :timerstate="timerState"
      :currentTimer="currentTimer"
      :color="color"
      :resetPlease="resetPlease"
      @time-tick="$emit('time-tick')"
    />
    <div class="circle">
      <div class="time_left">
        {{ timer[activeTimer].toFixed(2).replace(".", ":") }}
      </div>
      <div class="pause_btn" @click="toggleTimer">{{ timerBtnLabel }}</div>
    </div>
  </div>
</template>
<script>
import CircleTimer from "./CircleTimer.vue";
export default {
  name: "Timer",
  emits: ["time-tick", "toggle-timer"],
  components: {
    CircleTimer,
  },
  props: {
    color: {
      type: Object,
    },
    timer: {
      type: Object,
    },
    currentTimer: {
      type: Number,
    },
    activeTimer: {
      type: String,
    },
    timerState: {
      type: Boolean,
    },
    resetPlease: {
      type: String,
    },
  },
  computed: {
    timerBtnLabel() {
      return this.timerState ? ">PAUSE<" : ">START<";
    },
    theTimerState() {
      return this.timerState ? false : true;
    },
  },
  methods: {
    toggleTimer() {
      this.$emit("toggle-timer", this.theTimerState);
    },
  },
};
</script>
<style lang="sass" scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;900&display=swap')
$family: 'Roboto', sans-serif
$color: #d9e2ff
$gradient: linear-gradient(to left, #333 50%, #eee 50%)

.container
  width: 100%
  aspect-ratio: 1/1
  display: flex
  justify-content: center
  align-items: center
  position: relative

  .circle
    border-radius: 50%
    background: rgb(38,43,83)
    background: linear-gradient(330deg, rgba(38,43,83,1) 31%, #151932 63%)
    height: 80%
    width: 80%
    display: flex
    flex-direction: column
    align-items: center
    justify-content: center
    position: relative

    div
      z-index: 1
      font-family: $family
      color: $color

    .time_left
      font-size: 5.2em
      font-weight: 700

    .pause_btn
      font-size: 0.85em
      letter-spacing: 0.75em
      transform: translateY(1.5em)
      text-transform: uppercase

      &:hover
        cursor: pointer

    &:before
      content: ''
      position: absolute
      width: 90%
      height: 90%
      background: #151932
      border-radius: 50%
</style>
