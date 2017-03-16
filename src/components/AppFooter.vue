<template lang="pug">
  div.app-footer
    span.app-footer__love Made With Love by @judgeyboy89
    span.app-footer__social Github, Twitter
</template>

<script>
  export default {

  }
</script>

<style lang="sass">
  @import ../sass/colors

  .app-footer
    position: absolute
    bottom: 0
    display: flex
    height: 40px
    font-size: 1em
    justify-content: space-between
    width: 40rem
    margin: 50px auto

  .app-footer__love
    color: $off-white

  .app-footer__social
    color: $soft-red
</style>
