<template lang="pug">
  div.letter-display
    div.alphabet-letters(v-for="writtenLetter in lastThreeLetters")
      label.alphabet-input__display {{writtenLetter}}
</template>

<script>
  export default {
    name: 'LetterDisplay',
    props: ['letters'],
    computed: {
      lastThreeLetters(){
        if(this.letters.length <= 3){
          return this.letters;
        }
        return this.letters.slice(-3);
      }
    }
  }
</script>

<style lang="sass">
  @import ../sass/colors
  
  .alphabet-input__display
    font-size: 4em
    color: $soft-red
</style>
