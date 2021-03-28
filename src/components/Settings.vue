<template>
  <div>
    <span>
      <font-awesome-icon @click="showParams" icon="cog" />
    </span>
  </div>
  <ParamsModal :color="color" v-if="paramsOn" @close_modal="close" />
</template>
<script>
import ParamsModal from "./ParamsModal.vue";
export default {
  name: "Settings",
  emits: ["refresh"],
  components: {
    ParamsModal,
  },
  props: {
    color: {
      type: Object,
    },
  },
  data() {
    return {
      paramsOn: false,
    };
  },
  methods: {
    showParams() {
      this.paramsOn = !this.paramsOn;
    },
    close(d) {
      this.paramsOn = false;
      this.$emit("refresh", d);
    },
  },
};
</script>
<style lang="sass" scoped>
div
  font-size: 1.5em
  color: #7a7f9d
  margin-top: .5em
  display: flex
  justify-content: center

  span
    transform: rotate3d(0,0,1, 0deg) scale(1)
    opacity: 0.7
    transition: 0.25s all ease-in-out

    &:hover
      position: relative
      cursor: pointer
      opacity: 1
      transform: rotate3d(0,0,1, 90deg) scale(1.25)
</style>