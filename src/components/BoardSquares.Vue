<template>
    <div :class="['square', isLight ? 'light' : 'dark']">
    </div>
  </template>
  
  <script>
  export default {
    props: {
      isLight: {
        type: Boolean,
      }
    }
  }
  </script>
  
  <style>
  .square {
    /* temporary values to size the squares */
    width: 9vw; 
    height: 9vw; 
  }
  
  .light {
    background-color: var(--light-square);
  }
  
  .dark {
    background-color: var(--dark-square);
  }
  </style>