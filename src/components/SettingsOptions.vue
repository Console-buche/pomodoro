<template>
  <div class="option_container">
    <span>{{ option_name }}</span>
    <ul>
      <li
        v-for="d in option_data"
        :key="d"
        :class="[
          option_type,
          currentSelection == d ? `${option_type}--selected` : '',
          `${option_type}--${d}`,
        ]"
        @click="pickThis(d, option_type)"
      ></li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "SettingsOptions",
  emits: ["settings-font-color"],
  data() {
    return {
      selected: null,
      currentSelection: null,
      pink: "#fb6f70",
      purple: "#d983f2",
      lightblue: "#6ff3f8",
    };
  },
  props: {
    option_name: {
      type: String,
      default: "none",
    },
    option_data: {
      type: Array,
    },
    option_type: {
      type: String,
    },
  },
  methods: {
    pickThis(d, type) {
      this.currentSelection = d;
      if (type == "color") {
        const payload = { name: d, hex: this[d] };

        this.$emit("settings-font-color", {
          type: type,
          user_setting: payload,
        });
      } else if (type == "font") {
        this.$emit("settings-font-color", { type: type, user_setting: d });
      }
    },
  },
};
</script>
<style lang="sass" scoped>
.option_container
  margin: 10px
  display: flex
  justify-content: space-between
  width: 100%
  border-top: 1px solid #7a7f9d
  padding-top: 1.5em
  align-items: center

span

  text-transform: uppercase
  letter-spacing: 2px
  font-size: 0.6em
  color: black
  font-weight: bold

ul
  display: flex
  list-style-type: none
  margin: 0
  align-items: center

li
  margin-right: 10px
  display: flex
  box-sizing: border-box

.color, .font
  height: 45px
  width: 45px
  border-radius: 50%
  position: relative
  display: flex
  align-items: center
  &:hover
    cursor: pointer
    transform: scale(1.075)

.color--pink
  background: #fb6f70
.color--lightblue
  background: #6ff3f8
.color--purple
  background: #d983f2

.color--selected
  &:after
    content: '✔'
    position: absolute
    width: 100%
    color: #151a30

.font--fantasy
  font-family: fantasy

.font
  background: #eef0fd
  display: flex
  justify-content: center
  align-items: center
  &::after
    content: 'Aa'
    font-size: 0.6em

.font--selected
  &::after
    background: #151a30
    border-radius: 50%
    color: white
    height: 100%
    width: 100%
    display: flex
    justify-content: center
    align-items: center

.font--roboto
  font-family: 'Roboto'

.font--cursive
  font-family: cursive
</style>