<template lang="pug">
  div.wrapper
    page-title
    p.
      Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
      tempor incididunt ut labore et dolore magna aliqua.

    div.inner-wrapper
      div(v-show="isStopped")
        p Warm up your fingers! when you're ready...click start
        alpha-button(@click="startChallenge") Start Challenge

      div.alphabet-container(v-show="isInProgress")
        letter-display(:letters="matchedLetters")
        alphabet-input(:letter="letter", :onMatch="checkProgress")
        letter-display(:letters="letters")


      div(v-show="isCompleted")
        h2 Congratulations!
        p.
          You've completed the Alphabet-on-Keyboard challenge
          in {{ completedTimeInSeconds }} seconds.
        alpha-button(@click="restartGame") Play Again


    app-footer
</template>

<script>
  const ALPHABET = "abcdefghijklmnopqrstuvwxyz";

  import PageTitle from './PageTitle.vue'
  import LetterDisplay from './LetterDisplay.vue'
  import AlphabetInput from './AlphabetInput.vue'
  import AlphaButton from './AlphaButton.vue'
  import AppFooter from './AppFooter.vue'

  export default {
    name: 'App',
    data(){
      return {
        abc: '',
        gameState: 'stopped',
        interval: null,
        timeInHundredthOfASecond: 0,
        startTime: null,
        endTime: null,
        letter: 'a',
        letters: ALPHABET.split(''),
        matchedLetters: []
      }
    },
    computed: {
      isStopped(){
        return this.gameState === 'stopped';
      },
      isInProgress(){
        return this.gameState === 'inProgress';
      },
      isCompleted(){
        return this.gameState === 'completed';
      },
      completedTimeInSeconds(){
        return (this.endTime - this.startTime) / 1000 ;
      },
      currentTimeInSeconds(){
        return this.timeInHundredthOfASecond / 10;
      }
    },
    methods: {
      restartGame(){
        this.gameState = 'stopped';
        this.timeInHundredthOfASecond = 0;
        this.startTime = null;
        this.endTime = null;
        this.letter = 'a';
        this.letters = ALPHABET.split('');
        this.matchedLetters = [];
      },
      startChallenge(){
        this.startTime = Date.now();
        this.timer();
        this.gameState = 'inProgress';
      },
      // Todo: perhaps change method name to onLetterMatch?
      checkProgress(){
        let nextLetter = this.getNextLetter(this.letter);
        this.letters.shift();
        this.matchedLetters.push(this.letter);
        if(!nextLetter){
          this.endTime = Date.now();
          clearInterval(this.interval);
          this.gameState = 'completed';
        } else {
          this.letter = nextLetter;
        }
      },
      getNextLetter(currentLetter){
        // todo: handle z (last letter of alphabet case)
        return ALPHABET[ALPHABET.indexOf(this.letter) + 1];
      },
      timer(){
        this.interval = setInterval(this.updateTime, 100);
      },
      updateTime(){
        this.timeInHundredthOfASecond++;
      },

    },
    components: {
      PageTitle,
      LetterDisplay,
      AlphabetInput,
      AlphaButton,
      AppFooter
    }

  }
</script>

<style lang="sass">
  @import '../sass/main'

  .wrapper
    width: 40rem
    margin: 50px auto

  .inner-wrapper
    margin-top: 30px

  .alphabet-container
    display: flex
    width: 100%
    height: 5em

</style>
