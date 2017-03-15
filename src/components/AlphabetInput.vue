<template lang="pug">
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
        }
        this.clearInput();
      },
      clearInput(){
        this.input = '';
      }
    }
  }
</script>

<style lang="sass">

</style>
