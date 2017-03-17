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
    margin-top: 20px
    border: none
    padding: 0.3125em .625em
    font-family: 'Droid Sans', sans-serif
    font-size: 1em
    background: $soft-red
    color: $off-white
    cursor: pointer
    box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.24), 0 0 2px 0 rgba(0, 0, 0, 0.12)

    &:hover
      border-color: $off-white
      color: $off-white
      box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.24), 0 0 8px 0 rgba(0, 0, 0, 0.12)


</style>
