<template>
<div>
  <div class="column large">
    <GameSelection></GameSelection>
    <Timer></Timer>
  </div>
</div>
</template>

<script>
  import GameSelection from './GameSelection.vue'
  import Timer from './Timer.vue'
  export default {
  name: 'GameTracker',
  components: {
    GameSelection,
    Timer,
  }
  }


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>


