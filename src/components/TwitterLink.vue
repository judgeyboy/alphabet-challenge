<template lang="pug">
  a(:href="'https://twitter.com/intent/tweet?text=' + text + '&url=https://alphabet-challenge.herokuapp.com&hashtags=alphabet,challenge'" target="__blank").twitter-button
    i.fa.fa-twitter
</template>

<script>
export default {
  name: 'TwitterLink',
  props: ['completedTime'],
  computed: {
    text(){
      return 'Yes! ' + this.completedTime + ' Seconds! How quickly can you type the alphabet on your keyboard?';
    }
  }
}
</script>

<style lang="sass">
  @import ../sass/colors

  .twitter-button
    text-decoration: none
    margin-top: 20px
    margin-left: 10px
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
