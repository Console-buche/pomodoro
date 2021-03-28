<template>
  <h3>Time (minutes)</h3>
  <div>
    <ul>
      <li>
        <span>pomodoro</span>
        <input
          @change="pickThis('pomodoro')"
          v-model="pomodoro"
          type="number"
        />
      </li>
      <li>
        <span>pause courte</span>
        <input
          @change="pickThis('pause_courte')"
          v-model="pause_courte"
          type="number"
        />
      </li>
      <li>
        <span>pause longue</span>
        <input
          @change="pickThis('pause_longue')"
          v-model="pause_longue"
          type="number"
        />
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "TimeSelect",
  emits: ["settings-time"],
  data() {
    return {
      pomodoro: 25,
      pause_courte: 5,
      pause_longue: 15,
    };
  },
  methods: {
    pickThis(t) {
      this.$emit("settings-time", {
        type: t,
        user_setting: parseInt(this[t], 10),
      });
    },
  },
};
</script>
<style lang="sass" scoped>
h3
  text-align: left
  font-weight: bold
  font-size: 0.6em
  letter-spacing: 3px
  text-transform: uppercase
  margin-left: 10px
  color: black
ul
  list-style-type: none
  margin: 0
  padding: 0
  display: flex
  width: 100%
  justify-content: space-around
  height: 100%

  li
    display: flex
    flex-direction: column
    margin: 10px
    align-items: flex-start

    span
      font-size: 0.5em
      font-weight: bold
      padding: 5px

    input
      width: 100%
      height: 3em
      padding: 1em
      box-sizing: border-box
      font-weight: bold
      font-size: 0.65em
      background: #eef1fa
      border: none
      border-radius: 10px
      user-select: none
      outline: none
</style>