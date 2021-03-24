<template>
  <div class="container">
    <CircleTimer />
    <div class="circle">
      <div class="time_left">15:00</div>
      <div class="pause_btn">pause</div>
    </div>
  </div>
</template>
<script>
import CircleTimer from "./CircleTimer.vue";
export default {
  name: "Timer",
  components: {
    CircleTimer,
  },
  props: {
    color: {
      type: String,
    },
  },
};
</script>
<style lang="sass" scoped>
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

    &:before
      content: ''
      position: absolute
      width: 90%
      height: 90%
      background: #151932
      border-radius: 50%
</style>
