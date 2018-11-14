<template>
  <div id="game-of-life">
    <div class="logos-container">
      <img class="theodo-logo" alt="Theodo logo" src="./assets/theodo-logo.png">
      <img class="vue-logo" alt="Vue logo" src="./assets/vue-logo.png">
      <grid :rows=row_count :cols='3*row_count' :alive-cells-map="aliveCellsMapApp" />
    </div>
  </div>
</template>

<script>
import Cell from './Cell.vue'
import Grid from './Grid.vue'

const initial_init_row = 30;
export default {
  name: 'GameOfLife',
  components:{
    Cell,
    Grid
  },
  data: function() {
    return {row_count : initial_init_row,
            aliveCellsMapApp: {
              R24C55: true,
              R12C24: true,
              R22C18: true,
              R7C25: true,
              R11C76: true,
}}
  }
}
</script>

<style>
#game-of-life {
  padding: 60px 40px;
  position: relative;
}
.logos-container {
  position: absolute;
  top: 0;
  left: 0;
}
.logos-container img {
  height: 40px;
}
.logos-container img + img {
  margin-left: 5px;
}
</style>
