<template>
   <div class="chessboard">
        <div v-for="rank in 8" :key="'rank' + rank" class="rank">
            <BoardSquares 
            v-for="file in 8" 
            :key="'file' + file" class="file"
            :isLight="(rank + file) % 2 == 0"
            :coordinate="getCoordinate(file, rank)"
            @square-clicked="emitHistory"
            />
        </div>
    </div>
  </template>
  
  <script>
  import BoardSquares from './BoardSquares.vue';
  
  export default {
    components: {
      BoardSquares
    },
    methods: {
      getCoordinate(file, rank){

        // file: a to h
        const fileLetter = String.fromCharCode(96 + file); // one before 'a' (97)

        // rank: 1 to 8
        const rankNumber = 9 - rank;

        const coordinate = fileLetter + rankNumber;

        return coordinate;
      },
      emitHistory(coordinate){
        this.$emit('emitHistory', coordinate);
      }
    }
  }
  </script>
  
  <style>
  .chessboard {
    display: flex;
    flex-direction: column;
  }
  
  .rank {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  </style>