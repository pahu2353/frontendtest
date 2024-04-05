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
  </style>