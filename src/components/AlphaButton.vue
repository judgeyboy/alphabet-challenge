<template lang="pug">
  button.alpha-button(
    type="button"
    name="button"
    @click="$emit('click')")
    slot

</template>

<script>
  export default {
    name: 'AlphaButton'
  }
</script>

<style lang="sass" scoped>
  @import ../sass/colors

  .alpha-button
    border-radius: .25em
    border: .0625em solid $soft-red
    padding: 0.3125em .625em
    font-family: 'Droid Sans', sans-serif
    font-size: 1em
    background: transparent
    color: $soft-red
    cursor: pointer

    &:hover
      border-color: $off-white
      color: $off-white


</style>
