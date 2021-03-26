<template>
  <div class="option_container">
    <span>{{ option_name }}</span>
    <ul>
      <li
        v-for="data in option_data"
        :key="data"
        :class="[
          option_type,
          currentSelection == data ? `${option_type}--selected` : '',
          `${option_type}--${data}`,
        ]"
        @click="pickThis(data)"
      ></li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "SettingsOptions",
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
  data() {
    return {
      selected: null,
      currentSelection: null,
    };
  },
  methods: {
    pickThis(d) {
      this.currentSelection = d;
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

    & .color--pink
        background: #fb6f70
    & .color--lightblue
        background: #6ff3f8
    & .color--purple
        background: #d983f2

    & .font--selected
    & .font
        background: #eef0fd
        display: flex
        justify-content: center
        align-items: center

        &::after
            content: 'Aa'
            font-size: 0.6em

.color--selected
    &:after
        content: '✔'
        position: absolute
        width: 100%
        color: white

.font--selected
    &::after
        content: 'Aa'
        font-size: 0.6em
        background: #151a30
        border-radius: 50%
        color: white
        height: 100%
        width: 100%
        display: flex
        justify-content: center
        align-items: center

.color:hover:after
    color: white

.font--fantasy
    font-family: fantasy

.font--roboto
    font-family: 'Roboto'

.font--cursive
    font-family: cursive
</style>