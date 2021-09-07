<template>
<div>
  <div class="row">
    <div class="column large" style="max-width: 250px;">
      Select Game:<br>
      <select class="game_selection" id="game_select">
      </select>
    </div>
    <div class="column small" style="max-width: 250px;">
        Add Game:<br>
        <div class ="row" >
          <input TYPE="text" id = "GameText" SIZE=20 class = "game_selection">
          <img id="GSSButton" alt="Game_Submit" src="../assets/tick.svg" v-on:click="AddValue"/>
        </div>
    </div>

  </div>
</div>
</template>

<script>

  export default {
  name: 'GameSelection',
  methods: {
          //Add Game to Game Select
    AddValue: function(){
      var option = document.createElement("option");
      option.text = document.getElementById("GameText").value;
      if (option.text != ""){
        games.push(option.text);
      }
      document.getElementById("GameText").value = "";
      LoadSelect();
    }

  }
}

  let games =["Select"];

  function LoadSelect(){
    var list = document.getElementById("game_select");
    var length = list.options.length;
    for (var i = length-1; i >= 0; i--) {
      list.options[i] = null;
    }

    for(var index in games) {
      list.options[list.options.length] = new Option(games[index], index);
    }
  }


window.onload = LoadSelect;
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


  .game_selection {
    padding: 10px;
    text-align: left;
    float: center;
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


