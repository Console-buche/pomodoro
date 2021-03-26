<template>
  <div>
    <button>Apply</button>
  </div>
</template>
<script>
export default {
  name: "ApplyButton",
};
</script>
<style lang="sass" scoped>
div
    display: flex
    justify-content: center
    align-items: center
    height: 2em

    button
        height: 100%
        width: -webkit-fit-content
        transform: translateY(2.75em)
        outline: none
        border: none
        font-size: .75em
        background: #f87070
        border-radius: 25px
        padding: 15px 40px
        color: #fff
</style>