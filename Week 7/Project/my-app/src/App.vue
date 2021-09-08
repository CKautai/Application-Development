<template>

  <div>
    <div class="header">
    <h1>Game Time Tracker</h1>
  </div>
    <Navigation></Navigation>
    <GameTracker></GameTracker>
  </div>
</template>

<script>


import GameTracker from './components/GameTracker.vue'
import Navigation from './components/Navigation.vue'


export default {
  name: 'App',
  components: {
    GameTracker,
    Navigation,
  },


}
</script>

<style>
#app {
      box-sizing: border-box;
      font-family: 'Courier New', monospace;
}


  body {
    text-align: center;
    background-color: #141c33;
    color: #ffffff;
  }



  /* Style the header */
  .header {
    text-align: center;
    font-size: 35px;
    font-weight: 900;
    color: #FF5733;
    text-shadow: 0 0 0px #DEE2EC, 0 0 50px #FF5733;
  }

  /* Container for flexboxes */
  .row {
    display: -webkit-flex;
    display: flex;
    text-align: center;
    float:center;

  }

  /* Create three unequal columns that sits next to each other */
  .column {
    padding: 10px;
    text-align: center;
    max-width: 1000px;
    margin: auto;

  }

  /* small column */
  .column.small {
    -webkit-flex: 1;
    -ms-flex: 1;
    flex: 1;
  }

  /* medium column */
  .column.medium {
    -webkit-flex: 2;
    -ms-flex: 2;
    flex: 2;
  }

  /* large column */
  .column.large {
    -webkit-flex: 3;
    -ms-flex: 3;
    flex: 3;
  }

  /* Style the footer */
  .footer {
    padding: 10px;
    text-align: center;
  }

  /* Responsive layout - makes the three columns stack on top of each other instead of next to each other */
  @media (max-width: 600px) {
    .row {
      -webkit-flex-direction: row;
      flex-direction: row;
      text-align: center;
    }
  }
</style>
