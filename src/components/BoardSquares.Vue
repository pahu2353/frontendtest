<template>
    <div :class="['square', isLight ? 'light' : 'dark', isClicked ? 'clicked' : '']" @click="highlightSquare">
    </div>
  </template>
  
  <script>
  export default {
    props: {
      isLight: {
        type: Boolean,
      },
      coordinate: {
        type: String,
      },
    },
    data(){
      return {
        isClicked: false,
      };
    },
    methods: {
      highlightSquare(){
        this.isClicked = !this.isClicked;
        this.$emit('square-clicked', this.coordinate);
      }
    },
  }
  </script>
  
  <style>
  .square {
    /* temporary values to size the squares */
    width: 6vw; 
    height: 6vw; 
  }
  
  /* colours for board */
  .light {
    background-color: var(--light-square);
  }
  
  .dark {
    background-color: var(--dark-square);
  }

  .light.clicked {
    background-color: var(--highlight-light-square);
  }

  .dark.clicked {
    background-color: var(--highlight-dark-square);
  }

  @media (max-width: 600px){
    .square {
      width: 11vw;
      height: 11vw;
    }
  }

  @media (min-width: 600px){
    .square {
      width: 10vw;
      height: 10vw;
    }
  }

  @media (min-width: 768px){
    .square {
      width: 8vw;
      height: 8vw;
    }
  }

  @media (min-width: 992px){
    .square {
      width: 6.5vw;
      height: 6.5vw;
    }
  }

  /* laptops (default) */
  @media (min-width: 1200px){
    .square {
      width: 6vw;
      height: 6vw;
    }
  }

  /* desktop displays */
  @media (min-width: 1920px) {
  .square {
      width: 5.5vw;
      height: 5.5vw;
    }
  }
  </style>