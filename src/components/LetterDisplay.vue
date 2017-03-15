<template lang="pug">
  div.letters-display
    div.letter(v-for="letter in letters") {{letter}}
</template>

<script>
  export default {
    name: 'LetterDisplay',
    props: ['letters']
  }
</script>

<style lang="sass">
  @import ../sass/colors

  .letters-display
    display: flex
    align-items: center

  .letter
    font-size: 2em
    color: $soft-red

</style>
