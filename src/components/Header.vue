<template>
  <div>
    <ul>
      <li class="active">pomodoro</li>
      <li>short break</li>
      <li>long break</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "Header",
  props: {
    color: {
      type: String,
    },
  },
};
</script>
<style lang="sass" scoped>
div
    display: flex
    justify-content: center
    color: #4a4e67
    font-weight: bold
    ul
        list-style-type: none
        padding: 0
        display: flex
        align-items: center
        justify-content: center
        background-color: #151932
        border-radius: 50px
        li
            padding: 20px
            position: relative
.active
    background-color: #fa7070
    color: #6b3a4c
    margin: 3px
    border-radius: 30px
</style>