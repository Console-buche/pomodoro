<template>
  <div :class="font">
    <ul>
      <li
        v-for="option in timerOptions"
        :key="option.id"
        @click.stop="pick"
        :data-id="option.name"
        :class="[
          { active: activeTimer == option.name },
          { [color.name]: activeTimer == option.name },
        ]"
      >
        {{ option.name }}
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "Header",
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
        { name: "pomorodo", id: 1 },
        { name: "pause courte", id: 2 },
        { name: "pause longue", id: 3 },
      ],
      activeTimer: "pomodoro",
    };
  },
  methods: {
    pick(e) {
      console.log(e);
      let el = e.target.dataset.id;
      this.activeTimer = el;
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
    li
      padding: 20px
      position: relative
      white-space: nowrap
      border-radius: 30px
      margin: 3px

    &:hover
      cursor: pointer

.active
  color: #6b3a4c
</style>