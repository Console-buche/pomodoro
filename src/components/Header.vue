<template>
  <div :class="font">
    <ul>
      <li
        v-for="option in timerOptions"
        :key="option.id"
        @click.stop="pick"
        :data-id="option.name"
        :ref="option.name"
        :class="[{ active: activeTimer == option.name }]"
      >
        {{ option.name }}
      </li>
      <li
        :class="['underlight', (backgroundColor = `${color.name}`)]"
        :style="{
          width: `${underlight_width}px`,
          height: `${underlight_height}px`,
          left: `${transform_origin_x}px`,
        }"
      ></li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "Header",
  emits: ["change-timer-mode"],
  props: {
    color: {
      type: Object,
    },
    font: {
      type: String,
    },
  },
  data() {
    return {
      timerOptions: [
        { name: "pomodoro", id: 1 },
        { name: "pause courte", id: 2 },
        { name: "pause longue", id: 3 },
      ],
      activeTimer: "pomodoro",
      underlight_width: 0,
      underlight_height: 0,
      transform_origin_x: 0,
    };
  },
  mounted() {
    this.moveUnderline();
  },
  methods: {
    pick(e) {
      let el = e.target.dataset.id;
      this.activeTimer = el;
      this.moveUnderline();
      this.$emit("change-timer-mode", this.activeTimer);
    },
    moveUnderline() {
      const currentLi = this.$refs[this.activeTimer];
      const w = window.getComputedStyle(currentLi);
      const box_x = parseInt(w.width, 10) + parseInt(w.padding) * 2;
      const box_y = parseInt(w.height, 10) + parseInt(w.padding) * 2;
      this.underlight_width = box_x;
      this.underlight_height = box_y;
      this.transform_origin_x = currentLi.offsetLeft - parseInt(w.marginLeft);
    },
  },
};
</script>
<style lang="sass" scoped>
div
  display: flex
  justify-content: center
  color: #4a4e67
  font-weight: bold
  ul
    list-style-type: none
    padding: 0
    display: flex
    align-items: center
    justify-content: center
    background-color: #151932
    border-radius: 50px
    position: relative
    li
      padding: 20px
      position: relative
      white-space: nowrap
      border-radius: 30px
      margin: 3px
      z-index: 2
      user-select: none

    &:hover
      cursor: pointer

.underlight
  position: absolute
  border-radius: 30px
  z-index: 1
  box-sizing: border-box
  transition: 0.35s all ease-in-out

.active
  color: #6b3a4c
  transition-property: all
  transition-duration: 0.1s
  transition-delay: 0.3s
</style>