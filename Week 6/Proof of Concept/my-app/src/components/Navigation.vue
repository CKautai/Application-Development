<template>
<div>
  <!-- Navigation -->

    <ul class="topnav">
      <li><a href="#">Tracker</a></li>
      <li><a href="#">History</a></li>
      <li><a href="#">Log in</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
</div>
</template>

<script>

  export default {
  name: 'Navigation',

  }


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
</style>


