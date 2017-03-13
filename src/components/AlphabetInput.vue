<template lang="pug">
  div.alphabet-input
    label.alphabet-input__display {{letter}}
    input(type='text' v-model="input" @keyup="checkInput")
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
          this.input = '';
        } else {
          this.input = '';
        }
      }
    }
  }
</script>

<style lang="sass">
  alphabet-input__display
    color: blue
</style>
