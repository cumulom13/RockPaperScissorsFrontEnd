<template>
    <table>
        <thead>
            <tr>
             
                <th>Player 1 Choice</th>
                <th>Player 2 Choice</th>
                <th>Winner</th>
            </tr>    
        </thead>
        <tbody>
            <tr v-for="row in rows" :key="row.count">
                <td>{{row.player1Choice}}</td>
                <td>{{row.player2Choice}}</td>
                <td>{{row.winner}}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    name: 'ResultTable',
    props: {
        rows: Array
    }
    }
</script>

<style>
table {
  font-family: 'Open Sans', sans-serif;
  width: 750px;
  border-collapse: collapse;
  border: 3px solid #44475C;
  margin: 10px 10px 0 10px;
}

table th {
  text-transform: uppercase;
  text-align: left;
  background: #44475C;
  color: #FFF;
  padding: 8px;
  min-width: 30px;
}

table td {
  text-align: left;
  padding: 8px;
  border-right: 2px solid #7D82A8;
}
table td:last-child {
  border-right: none;
}
table tbody tr:nth-child(2n) td {
  background: #D4D8F9;
}

</style>

