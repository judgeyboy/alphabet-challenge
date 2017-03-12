<template>
  <button class="alpha-button"
          @click="$emit('click')"
          type="button"
          name="button">
    <slot></slot>
  </button>
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
