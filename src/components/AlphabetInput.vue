<template lang="pug">
  input.alphabet-input(
    type='text'
    v-model="input"
    @input="checkInput"
    v-focus)
</template>

<script>

  export default {
    name: 'AlphabetInput',
    data(){
      return {
        input: ''
      }
    },
    props: ['letter', 'onMatch'],
    methods: {
      checkInput(){
        if (this.input === this.letter){
          this.onMatch();
        }
        this.clearInput();
      },
      clearInput(){
        this.input = '';
      }
    },
    directives: {
      focus: {
        inserted: function(el){
          el.focus()
        }
      }
    }
  }
</script>

<style lang="sass">
  @import ../sass/colors

  .alphabet-input
    border: none
    border-bottom: 2px solid $soft-red
    width: 2em
    font-size: 2em
    color: $soft-red
    background-color: transparent
    text-align: center
    outline: none

</style>
