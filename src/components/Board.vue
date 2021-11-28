<template>
  <div>Status: {{ nextPlayer }}</div>
  <div class="board">
    <div
      class="square"
      v-for="(square, index) in squares"
      :key="index"
      @click="handleClick(index)"
    >
      {{ square }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Board',
  data() {
    return {
      squares: ['', '', '', '', '', '', '', '', ''],
      nextPlayer: 'X',
    }
  },
  methods: {
    handleClick(index) {
      this.squares[index] = this.nextSquare()
    },
    nextSquare() {
      const xLength = this.squares.filter((square) => square === 'X').length
      const oLength = this.squares.filter((square) => square === 'O').length
      if (xLength > oLength) {
        this.nextPlayer = 'X'
        return 'O'
      } else {
        this.nextPlayer = 'O'
        return 'X'
      }
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
a {
  color: #42b983;
}
.board {
  display: grid;
  grid-template-columns: 50px 50px 50px;
  grid-template-rows: 50px 50px 50px;
  justify-content: center;
  border: 1px solid #42b983;
  width: fit-content;
  margin: 40px auto;
  .square {
    width: 100%;
    height: 100%;
    border: 1px solid #42b983;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 30px;
    font-weight: bold;
  }
}
</style>
