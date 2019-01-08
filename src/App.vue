<template>
  <div id="app">
    <img class="img" alt="Vue logo" src="./assets/Rock-paper-scissors.png">
    <RockPaperScissors/>
  </div>
</template>

<script>
import RockPaperScissors from  './components/RockPaperScissors.vue';

export default {
  name: 'app',
  components: {
    RockPaperScissors
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: bisque;
}

.img{
  width: 400px;
  border-radius: 2px;
  box-shadow: 1px 1px 3px 1px rgba(0, 0, 0, 0.5);
  transition: width 1s;
}

</style>
