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
  .alpha-button
    border-radius: 4px
    border: 1px solid green
    padding: 5px 10px
    font: normal normal Arial
    background: transparent
    color: green
</style>
