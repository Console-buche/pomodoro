<template>
  <section>
    <Header
      :color="global_style.color"
      :font="global_style.font"
      @change-timer-mode="resetTimer"
    />
    <Timer
      :currentTimer="currentTimer"
      :activeTimer="activeTimer"
      :color="global_style.color"
      :timer="timer_settings"
      :timerState="timerState"
      :resetPlease="resetPlease"
      @time-tick="tick"
      @toggle-timer="toggleTimer"
    />
    <Settings :color="global_style.color" @refresh="refreshApp" />
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
        color: { name: "pink", hex: "#fb6f70" },
        font: "Roboto",
      },
      activeTimer: "pomodoro",
      timer_settings: {
        pomodoro: 15,
        pause_courte: 5,
        pause_longue: 25,
      },
      timer_backup: {
        pomodoro: 15,
        pause_courte: 5,
        pause_longue: 25,
      },
      timerState: false,
      resetPlease: "",
    };
  },
  computed: {
    currentTimer: function () {
      return this.timer_settings[this.activeTimer];
    },
  },
  methods: {
    resetTimer(e = "pomodoro") {
      let key = e.replace(" ", "_");
      this.timer_settings[key] = this.timer_backup[key];

      this.timerState = false;
      this.activeTimer = key;

      this.resetPlease += "again";
    },
    toggleTimer() {
      this.timerState = !this.timerState;
    },
    refreshApp(d) {
      console.log(d);
      this.global_style.color = d.color ? d.color : this.global_style.color;
      this.global_style.font = d.font ? d.font : this.global_style.font;

      //timer_settings
      const timer_settings = {
        pomodoro: d.pomodoro,
        pause_courte: d.pause_courte,
        pause_longue: d.pause_longue,
      };

      //safety type coercing, whatever to number
      let parseInt_timer_settings = Object.entries(timer_settings).reduce(
        function (accArray, nextTimer) {
          accArray[nextTimer[0]] = nextTimer[1];
          return accArray;
        },
        {}
      );

      //store parseInt timer settings, just in case
      this.timer_settings = { ...parseInt_timer_settings };
      this.timer_backup = { ...parseInt_timer_settings };

      this.timer_settings = { ...this.timer_backup };
      this.resetTimer();
    },
    tick() {
      if (this.timerState) {
        let decimals = Number(
          Math.abs(
            Math.floor(this.timer_settings[this.activeTimer]) -
              this.timer_settings[this.activeTimer]
          ).toFixed(2)
        );

        //ugly yet readble. Prefered this to minmaxing or ternary checking, although lengthy
        if (decimals == 0) {
          this.timer_settings[this.activeTimer] =
            this.timer_settings[this.activeTimer] - 0.41; //hardcoding ftw ?
        } else {
          this.timer_settings[this.activeTimer] =
            decimals > 0.6
              ? Math.floor(this.timer_settings[this.activeTimer]) + 0.6
              : this.timer_settings[this.activeTimer] - 0.01;
        }
      }
    },
  },
};
</script>
<style lang="sass">
section
  max-width: 400px
  width: 70vmax
  padding: 5vh

  background: rgb(38,43,83)
  background: radial-gradient(circle, #262b53 32%, #14162d 45%)

.lightblue
  background-color: #6ff3f8

.pink
  background-color: #fb6f70

.purple
  background-color: #d983f2

.fantasy
  font-family: fantasy

.roboto
  font-family: 'Roboto'

.cursive
  font-family: curvise
</style>
