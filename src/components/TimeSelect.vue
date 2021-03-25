<template>
  <h3>Time (minutes)</h3>
  <div>
    <ul>
      <li><span>pomodoro</span> <input type="number" value="25" /></li>
      <li><span>short break</span> <input type="number" value="5" /></li>
      <li><span>long break</span> <input type="number" value="15" /></li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "TimeSelect",
};
</script>
<style lang="sass" scoped>
h3
    text-align: left
    font-weight: bold
    font-size: 0.5em
    letter-spacing: 3px
    text-transform: uppercase
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