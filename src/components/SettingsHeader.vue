<template>
  <div class="settings_container">
    <h1>Settings</h1>
    <span @click="close" class="settings_container__close">x</span>
  </div>
</template>
<script>
export default {
  name: "SettingsHeader",
  methods: {
    close() {
      this.$emit("close_modal");
    },
  },
};
</script>
<style lang="sass" scoped>
.settings_container
  display: flex
  justify-content: space-between
  align-items: center
  padding: 20px 10px
  color: black
  position: relative

  h1
    font-weight: bold
    margin: 0

    &::after
      content: ''
      bottom: 0
      left: -10px
      width: calc(20px + 100%)
      border-bottom: 1px solid #7a7f9d
      position: absolute

.settings_container__close
  padding: 2.5px 10px
  border-radius: 2.5px
  transition: 0.15s all ease

  &:hover
    background: #14162d
    color: white
    cursor: pointer
</style>