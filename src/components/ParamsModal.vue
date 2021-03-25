<template>
  <div class="modal">
    <div>
      <SettingsHeader />
      <TimeSelect />
      <hr />
      <div>FONT</div>
      <hr />
      <div>COLOR</div>
    </div>
  </div>
</template>
<script>
import TimeSelect from "./TimeSelect.vue";
import SettingsHeader from "./SettingsHeader.vue";
export default {
  name: "ParamsModal",
  components: {
    TimeSelect,
    SettingsHeader,
  },
};
</script>
<style lang="sass" scoped>
$height: 400px
.modal

    position: absolute
    width: $height*1.5
    height: $height
    top: 0
    bottom: 0
    left: 0
    right: 0
    margin: auto
    z-index: 100
    background: white
    border-radius: 20px

    &>div
        width: 100%
        height: 100%
        padding: 20px 10px
        box-sizing: border-box
</style>