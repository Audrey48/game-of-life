<template>
  <div class="grid__container" :style="`--rows:${rows}; --columns:${cols};`">
    <cell :is-alive="isCellAlive(cellule)" v-for="cellule in cellsCount" :key="cellule"/>
  </div>
</template>

<script>
import Cell from './Cell.vue'
export default {name: 'Grid',
  props: {
  rows: Number.required,
  cols: Number.required,
  aliveCellsMap: Object
  },
  components:{
    Cell,
  },
  computed: {
    cellsCount: function() {
      return this.rows*this.cols
    },
  },
  methods: {
    isCellAlive: function(index) {
      console.log(index)
      console.log(this.getCellIdFromIndex(index, this.cols))
      console.log(this.aliveCellsMap[this.getCellIdFromIndex(index, this.cols)])
        return this.aliveCellsMap[this.getCellIdFromIndex(index, this.cols)]
    },
    getCellId: function(row, column) {
      return `R${row}C${column}`
    },
    getCellIdFromIndex: function(cellIndex, columnsCount) {
      const row = Math.floor((cellIndex - 1) / columnsCount)
      const column = (cellIndex - 1) % columnsCount
      return this.getCellId(row, column)
    }

  }
}

</script>

<style>
.grid__container {
  width: 90vw;
  height: 30vw;
  margin: auto;
  display: grid;
  border: solid 1px black;
  background-color: black;
  grid-gap: 1px;
  grid-template-columns: repeat(var(--columns), 1fr);
  grid-template-rows: repeat(var(--rows), 1fr);
}
</style>