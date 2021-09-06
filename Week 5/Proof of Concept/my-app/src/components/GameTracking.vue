<template>
<div>
  <div class="header">
    <h1>Game Time Tracker</h1>
  </div>
  <!-- Navigation -->

    <ul class="topnav">
      <li><a href="#">Tracker</a></li>
      <li><a href="#">History</a></li>
      <li><a href="#">Log in</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
    <div class="column large">
      <!-- Game Selection -->
      <div class="row">
        <div class="column large" style="max-width: 250px;">
          Select Game:<br>
          <SELECT class="game_selection" id="game_select">
            <OPTION VALUE="Select">Select</OPTION>
            <OPTION VALUE="Assassins Creed">Assassins Creed</OPTION>
            <OPTION VALUE="Sea of Thieves">Sea of Thieves</OPTION>
            <OPTION VALUE="Final Fantasy">Final Fantasy</OPTION>
            <OPTION VALUE="Elder Scrolls">Elder Scrolls</OPTION>
            <OPTION VALUE="Civilization">Civilization</OPTION>
          </SELECT>
        </div>
        <div class="column small" style="max-width: 250px;">
            Add Game:<br>
            <div class ="row" >
              <INPUT TYPE="text" id = "GameText" SIZE=20 class = "game_selection">
              <img id="GSSButton" alt="Game_Submit" src="./assets/tick.svg" onclick="AddValue()">
            </div>
        </div>

      </div>
      <div class="row">
        <!-- Timer -->
        <div class="column small">
          <span class="time" id="display">00:00:00</span>
        </div>
      </div>
      <div class="row">
        <!-- Start -->
        <div class="column small">
          <button class="buttonPlay">
            <img id="playButton" alt="Play" src="./assets/play.svg" />

            <img id="pauseButton" alt="Pause" src="./assets/pause.svg" />
          </button>
        </div>
        <!-- Submit -->
        <div class="column small">
          <button class="buttonSubmit">
            <img id="submitButton" alt="Submit" src="./assets/save.svg" />
          </button>
        </div>
      </div>
    </div>
  <div class="footer">
    <p>By Caleb Kautai</p>
  </div>
</div>
</template>

<script>
  //Add Game to Game Select
    function AddValue(){
      var list = document.getElementById("game_select")
      var option = document.createElement("option");
      option.text = document.getElementById("GameText").value;
      if (option.text != ""){
        list.add(option);
      }
      document.getElementById("GameText").value = "";
    }



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
      startTime = Date.now() - elapsedTime;
      timerInterval = setInterval(function printTime() {
        elapsedTime = Date.now() - startTime;
        print(timeToString(elapsedTime));
      }, 10);
      showButton("PAUSE");
    }

    function pause() {
      clearInterval(timerInterval);
      showButton("PLAY");
    }


    // Display buttons

    function showButton(buttonKey) {
      const buttonToShow = buttonKey === "PLAY" ? playButton : pauseButton;
      const buttonToHide = buttonKey === "PLAY" ? pauseButton : playButton;
      buttonToShow.style.display = "block";
      buttonToHide.style.display = "none";
    }
    // Create event listeners

    let playButton = document.getElementById("playButton");
    let pauseButton = document.getElementById("pauseButton");


    playButton.addEventListener("click", start);
    pauseButton.addEventListener("click", pause);

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  body {
    text-align: center;
    background-color: #141c33;
    color: #ffffff;
  }

  /* Style the top navigation bar */
  .topnav {
    overflow: hidden;
    background-color: #333;
    text-align: center;
  }

  /* Style the topnav links */
  .topnav a {
    display: inline-block;
    color: #f2f2f2;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;

  }

  /* Change color on hover */
  .topnav a:hover {
    background-color: #ddd;
    color: #040F0F;
  }

  .topnav li{
    display: inline;
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

  .game_selection {
    padding: 10px;
    text-align: left;
    float: center;
  }

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
    display: none;
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
  #GSSButton {
    cursor: pointer;
    background: transparent;
    padding: 0;
    margin: auto;
    width: 40px;
    height: 40px;



  }
</style>
