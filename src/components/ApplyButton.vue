<template>
  <div>
    <button :class="color.name" @click="saveSettings">Apply</button>
  </div>
</template>
<script>
export default {
  name: "ApplyButton",
  props: {
    color: {
      type: Object,
    },
  },
  data() {
    return {};
  },
  methods: {
    saveSettings() {
      this.$emit("save-settings");
    },
  },
};
</script>
<style lang="sass" scoped>
div
  display: flex
  justify-content: center
  align-items: center
  height: 2em
  transition: 0.15s transform ease-out
  transform: translateY(2em)
  &:hover
    transform: translateY(2em) scale(1.05)

/*** TODO : animation scale du bouton shape SANS le texte ***/

button
  width: -webkit-fit-content
  border: none
  font-size: .75em
  border-radius: 25px
  padding: 15px 40px
  color: #fff

  &:hover
    cursor: pointer

  &:focus
    outline: none
</style>