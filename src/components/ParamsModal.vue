<template>
  <div class="modal">
    <div>
      <SettingsHeader @close_modal="close" />
      <TimeSelect />
      <div class="options">
        <SettingsOptions
          v-for="option in options"
          :option_name="option.name"
          :option_data="option.data"
          :option_type="option.type"
          :key="option"
        />
        <ApplyButton />
      </div>
    </div>
  </div>
</template>
<script>
import TimeSelect from "./TimeSelect.vue";
import SettingsHeader from "./SettingsHeader.vue";
import SettingsOptions from "./SettingsOptions.vue";
import ApplyButton from "./ApplyButton.vue";
export default {
  name: "ParamsModal",

  data() {
    return {
      options: [
        { name: "font", type: "font", data: ["roboto", "cursive", "fantasy"] },
        { name: "color", type: "color", data: ["pink", "lightblue", "purple"] },
      ],
    };
  },
  methods: {
    close() {
      this.$emit("close_modal");
    },
  },
  components: {
    TimeSelect,
    SettingsHeader,
    SettingsOptions,
    ApplyButton,
  },
};
</script>
<style lang="sass" scoped>
$height: 15em
.modal
  position: absolute
  width: 20.5em
  height: -webkit-fit-content
  height: -moz-fit-content
  height: fit-content
  top: 0
  bottom: 0
  left: 0
  right: 0
  margin: auto
  z-index: 100
  background: #fff
  border-radius: 20px

  &>div
    width: 100%
    height: 100%
    padding: 20px 10px

.options
  display: flex
  flex-direction: column
  align-items: center
  padding: 10px
</style>