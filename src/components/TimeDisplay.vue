<template lang="pug">
  div
    h2 {{time / 10}}
</template>

<script>
export default {
  name: 'TimeDisplay',
  props: ['time']
}
</script>

<style lang="sass">
</style>
