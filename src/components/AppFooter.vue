<template lang="pug">
  div.app-footer
    div.love
      span.app-footer__love Made With &nbsp;
      i.fa.fa-heart.app-footer__heart
      span.app-footer__love &nbsp;By&nbsp;
      a(href="https://twitter.com/judgeyboy89", target="__blank").app-footer__link @judgeyboy89
    a(href="https://github.com/judgeyboy/alphabet-challenge", target="__blank").app-footer__link
      i.fa.fa-github.fa-2x
</template>

<script>
  export default {
    name: 'AppFooter'
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
    color: $off-white

  .app-footer__heart
    color: $soft-red

  .app-footer__link
    color: $soft-red
    text-decoration: none

    &:visited
      color: $soft-red

</style>
