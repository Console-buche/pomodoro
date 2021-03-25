<template>
  <div id="nav"><router-link to="/">Pomodoro</router-link></div>
  <router-view />
</template>

<style lang="sass">
body
  margin: 0
  background: #14162d

#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50
  display: flex
  flex-direction: column
  align-items: center
  background: #14162d

#nav
  padding: 30px

  a
    font-weight: bold
    color: #2c3e50

    &.router-link-exact-active
      color: #42b983
</style>
