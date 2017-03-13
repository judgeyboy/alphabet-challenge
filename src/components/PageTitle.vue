<template lang="pug">
  h1.red The Alphabet-on-Keyboard Challenge!
</template>

<script>
export default {
  name: 'PageTitle'
}
</script>

<style lang="sass" scoped>
  @import ../sass/colors

  h1
    font-size: 3rem
    font-family: 'Kreon', serif
    margin: 0.8em 0

    &:hover
      font-size: 4rem
      transition: all 300ms ease-in-out

    &.red
      color: $soft-red
</style>
