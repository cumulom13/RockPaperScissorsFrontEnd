<template>
    <div>
        <button class="btn btn-primary"   @click="playRound">Play Round</button>
        <button class="btn btn-outline-secondary" @click="restartGame">Restart Game</button>
        <button class="btn btn-outline-info" @click="setComponentsVisibility(false)" >Show Full Game Information</button>
        <div class="table" v-if="tableVisible" >
            <p>Total Number of rounds played: {{count}}</p>
            <ResultTable :rows="roundsInformation"/>
        </div>
        <div v-else>
            <TotalResult/>
        </div>
    </div>
</template>


<script>
import axios from "axios";
import ResultTable from '@/components/ResultTable.vue';
import TotalResult from '@/components/TotalResult.vue';
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
    name: 'RockPaperScissors',
    components: {
        ResultTable,
        TotalResult
    },
    data() {
       return { roundsInformation: [],
       count: 0,
       tableVisible: true,
       globalResultVisible: false,
      
       }
    },
    methods:{
        playRound: function(){   
            axios.get('http://localhost:8090/rockPaperScissors/playRound')
            .then(response => {
            var  player1Choice = response.data.player1Choice;
            var player2Choice = response.data.player2Choice;
            var winner = response.data.winner;
            this.count++;
            this.roundsInformation.push({player1Choice, player2Choice, winner});
            })
        },
        restartGame: function(){
            this.count= 0;
            this.roundsInformation.splice(0, this.roundsInformation.length);
            this.setComponentsVisibility(true);
        },
        setComponentsVisibility: function(isVisible){
            this.tableVisible = isVisible;
        }
    }
}
</script>


<style>
.table{
  width: 50%;
  margin: 0 auto;
}

button{
    margin: 10px 5px ;
}
</style>
