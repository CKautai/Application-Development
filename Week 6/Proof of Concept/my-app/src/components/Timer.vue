<template>
<div>
  <div class="row">
    <!-- Timer -->
    <div class="column small">
      <span class="time" id="display">00:00:00</span>
    </div>
  </div>
  <div class="row">
    <!-- Start -->
    <div class="column small">
      <button>
        <img id="playButton" alt="Play" src="../assets/play.svg" v-on:click="InitStart" />
      </button>
    </div>
    <!-- Pause -->
    <div class="column small">
      <button>
        <img id="pauseButton" alt="Pause" src="../assets/pause.svg" v-on:click="InitPause" />
      </button>
    </div>
    <!-- Submit -->
    <div class="column small">
        <img id="submitButton" class="button" alt="Submit" src="../assets/save.svg" v-on:click="InitSubmit" />
    </div>
  </div>
</div>
</template>

<script>

  export default {
  name: 'Timer',

  methods: {
    InitStart: function() {
      start()
    },

    InitPause: function() {
      pause();
    },

    InitSubmit: function(){
      submit();
    }
  }


  }
    let playing = false;

    // Convert time to a format of hours, minutes, seconds, and milliseconds
    function timeToString(time) {
      let diffInHrs = time / 3600000;
      let hh = Math.floor(diffInHrs);

      let diffInMin = (diffInHrs - hh) * 60;
      let mm = Math.floor(diffInMin);

      let diffInSec = (diffInMin - mm) * 60;
      let ss = Math.floor(diffInSec);



      let formattedHH = hh.toString().padStart(2, "0");
      let formattedMM = mm.toString().padStart(2, "0");
      let formattedSS = ss.toString().padStart(2, "0");

      return `${formattedHH}:${formattedMM}:${formattedSS}`;
    }
    // Declare variables to use in our functions below

    let startTime;
    let elapsedTime = 0;
    let timerInterval;


    // Create function to modify innerHTML

    function print(txt) {
      document.getElementById("display").innerHTML = txt;
    }

    // Create "start", "pause" and "reset" functions
    function start() {
      if (!playing){
        startTime = Date.now() - elapsedTime;
        timerInterval = setInterval(function printTime() {
          elapsedTime = Date.now() - startTime;
          print(timeToString(elapsedTime));
        }, 10);
        playing = true;
      }
    }
    function pause() {
      if (playing){
        clearInterval(timerInterval);
        playing = false;
      }
    }

    function submit() {
      if (playing){
        pause();
      }

    }













</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>



  .time {
    font-weight: 300;
    font-size: 48px;
    background-color: #ddd;
    background: solid;
    border: #040F0F;
    border-width: 3px;
    color: #040F0F;
  }

  button {
    cursor: pointer;
    background: transparent;
    padding: 0;
    border: none;
    margin: 0;
    width: 100px;
    height: 100px;
  }

  #playButton {
    display: block;
    border: none;
  }

  #pauseButton {
    display: block;
    border: none;
  }

  #submitButton {
    cursor: pointer;
    background: transparent;
    padding: 0;
    border: none;
    margin: 0;
    width: 100px;
    height: 100px;
  }

</style>


