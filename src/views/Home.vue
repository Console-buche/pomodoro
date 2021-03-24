<template>
  <section>
    <Header :color="global_style.color" />
    <Timer :color="global_style.color" />
    <Settings :color="global_style.color" />
  </section>
</template>

<script>
import Header from "@/components/Header.vue";
import Timer from "@/components/Timer.vue";
import Settings from "@/components/Settings.vue";
export default {
  name: "Home",
  components: {
    Header,
    Timer,
    Settings,
  },
  data() {
    return {
      global_style: {
        color: "blue",
        fontFamily: "",
      },
    };
  },
};
</script>
<style lang="sass" scoped>
section
  max-width: 400px
  width: 70vmax
  padding: 5vh

  background: rgb(38,43,83)
  background: radial-gradient(circle, #262b53 40%, #1e2140 58%)
</style>
