<template>
  <svg>
    <circle
      :stroke="stroke"
      :stroke-width="strokeWidth"
      :fill="fill"
      :stroke-dasharray="`${startCircumference} ${startCircumference}`"
      :style="`stroke-dashoffset:${
        currentCircumference + startCircumference + elapsed
      }`"
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
  data() {
    return {
      stroke: "#fa7070",
      dashOffset: "0",
      strokeWidth: 10,
      fill: "transparent",
      geometry: {
        r: 150,
        cx: 200,
        cy: 200,
      },
      elapsedTime: 0,
    };
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
  },
  created() {
    const d = this; //watch out for setinterval this scope
    setInterval(function () {
      d.elapsedTime += 0.001;
    }, 10);
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
}
</style>