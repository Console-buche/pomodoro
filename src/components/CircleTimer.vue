<template>
  <svg>
    <circle
      :stroke="color.hex"
      :stroke-width="strokeWidth"
      :fill="fill"
      :stroke-dasharray="`${startCircumference} ${startCircumference}`"
      :style="`stroke-dashoffset:${dashOffsett}; transition: ${animSpeed}s stroke-dashoffset`"
      stroke-linecap="round"
      :r="normalizedRadius"
      :cx="geometry.cx"
      :cy="geometry.cy"
    />
  </svg>
</template>
<script>
export default {
  name: "CircleTimer",
  emits: ["time-tick"],
  props: {
    color: {
      type: Object,
    },
    timerstate: {
      type: Boolean,
    },
    currentTimer: {
      type: Number,
    },
    resetPlease: {
      type: String,
    },
  },
  data() {
    return {
      one_min_to_ms: 1 / 60,
      dashOffset: "0",
      strokeWidth: 10,
      fill: "transparent",
      geometry: {
        r: 150,
        cx: 200,
        cy: 200,
      },
      elapsedTime: 0, //percent
    };
  },
  watch: {
    resetPlease: function (o, n) {
      if (n !== o) {
        this.elapsedTime = 0;
      }
    },
  },
  computed: {
    normalizedRadius() {
      return this.geometry.r - this.strokeWidth * 2;
    },
    startCircumference() {
      return this.normalizedRadius * 2 * Math.PI;
    },
    currentCircumference() {
      return this.normalizedRadius * 2 * Math.PI;
    },

    elapsed() {
      return this.startCircumference * this.elapsedTime;
    },
    dashOffsett() {
      return this.currentCircumference + this.startCircumference + this.elapsed;
    },
    pomodoroTimer() {
      return this.one_min_to_ms / this.currentTimer;
    },
    animSpeed() {
      return 1 - this.pomodoroTimer;
    },
  },
  created() {
    const d = this; //watch out for setinterval this scope
    setInterval(function () {
      if (d.timerstate) {
        d.elapsedTime += d.pomodoroTimer;
        d.$emit("time-tick");
      }
    }, 1000);
  },
};
</script>
<style lang="scss" scoped>
svg {
  position: absolute;
  left: 0;
  top: 0;
  z-index: 1;
  height: 100%;
  width: 100%;
}
circle {
  // transition: stroke-dashoffset 0.35s;
  transform-origin: 50% 50%;
  transform: rotate3d(0, 0, 1, -90deg);
}
</style>