<template>
  <div class="cell" v-bind:class="isAlive?'alive':''"></div>
</template>

<script>
export default {name: 'Cell',
  props: {
  title: String,
  isAlive: Boolean
  },
}

</script>

<style>
.cell {
  background-color: white;
}
.alive {
  background-color: black;
}
</style>