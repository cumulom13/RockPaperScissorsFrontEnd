<template>
    <div>
        <p>Total Number of Rounds played: {{this.numberOfRounds}}</p>
        <p>Player 1 winner times: {{this.player1Winner}}</p>
        <p>Player 2 winner times: {{this.player2Winner}}</p>
        <p>Number of draws: {{this.draws}}</p>
        <p>To play again click on Restart Game</p>
    </div>
</template>


<script>
import axios from "axios";
 

export default {
    name: 'TotalResult',
    data() {
        return {
          numberOfRounds: 0,
          player1Winner: 0,
          player2Winner: 0,
          draws:0      
        }
    },
    mounted() {
         axios.get('http://localhost:8090/rockPaperScissors/getGlobalGameInformation')
                .then(response => {
                    this.numberOfRounds = response.data.totalNumberOfGames; 
                    this.player1Winner = response.data.player1WinnerTimes;
                    this.player2Winner = response.data.player2WinnerTimes;
                    this.draws = response.data.draws;
             })
    },

    
}
</script>


<style>

</style>
