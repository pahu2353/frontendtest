<template>
   <div class="chessboard">
        <div v-for="rank in 8" :key="'rank' + rank" class="rank">
            <BoardSquares 
            v-for="file in 8" 
            :key="'file' + file" class="file"
            :isLight="(rank + file) % 2 == 0"/>
        </div>
    </div>
  </template>
  
  <script>
  import BoardSquares from './BoardSquares.vue';
  
  export default {
    components: {
      BoardSquares
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
  }


  </style>