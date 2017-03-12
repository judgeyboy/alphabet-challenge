<template>
  <div>
    <h1>The Alphabet-on-Keyboard Challenge!</h1>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
      tempor incididunt ut labore et dolore magna aliqua.
      <alpha-button @click="foo">play</alpha-button>
    </p>

    <div v-show="isStopped">
      <p>Warm up your fingers! when you're ready...click start</p>
      <button type="button" @click="startChallenge">START CHALLENGE</button>
    </div>

    <div v-show="isInProgress">
      <alphabet-input :letter="letter" :onMatch="checkProgress" />
    </div>

    <div v-show="isCompleted">
      <h2>Congratulations!</h2>
      <p>You've completed the Alphabet-on-Keyboard challenge in {{ completedTimeInSeconds }} seconds.</p>
      <button type="button" @click="restartGame">Play Again</button>
    </div>

    {{currentTimeInSeconds}}
  </div>
</template>

<script>
  const ALPHABET = "abcdefgh".split('');

  import AlphabetInput from './AlphabetInput.vue'
  import AlphaButton from './AlphaButton.vue'

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
        letter: 'a'
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
      },
      startChallenge(){
        this.startTime = Date.now();
        this.timer();
        this.gameState = 'inProgress';
      },
      checkProgress(){
        let nextLetter = this.getNextLetter(this.letter);
        if(!nextLetter){
          this.endTime = Date.now();
          clearInterval(this.interval);
          this.gameState = 'completed';
        } else {
          this.letter = nextLetter;
        }
      },
      foo(){
        alert('fooo was pressed');
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
      AlphabetInput,
      AlphaButton
    }

  }
</script>

<style lang="sass">
  @import '../sass/main'
</style>
