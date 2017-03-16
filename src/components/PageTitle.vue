<template lang="pug">
  h1.red The Alphabet Challenge!
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

    &.red
      color: $soft-red
</style>
