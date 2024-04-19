<template>
    <!-- conditional styling based on square colour -->
    <div :class="['square', isLight ? 'light' : 'dark', isClicked ? 'clicked' : '']" @click="highlightSquare">
        <!-- labels should be opposite of square; light for dark squares and dark for light squares -->
        <div class="rankLabels" :class="[ isLight ? 'darkLabel' : 'lightLabel' ]" v-if="coordinate[0] === 'a'">
            {{ coordinate[1] }}
        </div>
        <div class="fileLabels" :class="[ isLight ? 'darkLabel' : 'lightLabel' ]" v-if="coordinate[1] === '1'">
            {{  coordinate[0] }}
        </div>
    </div>
  </template>
  
  <script setup> 
  import { ref, defineProps, defineEmits } from 'vue';
  const emits = defineEmits(['square-clicked']);

  const props = defineProps({
    isLight: {
      type: Boolean,
    },
    coordinate: {
      type: String,
    },
  })

  let isClicked = ref(false);

  const highlightSquare = () => {
    isClicked.value = !isClicked.value;
    emits('square-clicked', props.coordinate);
  }
  </script>
  
  <style>
  .square {
    /* temporary values to size the squares */
    width: 6vw; 
    height: 6vw; 
    position: relative;
  } 

  /* colours for board and all its states */
  .rankLabels {
    font-weight: 700;
    position: absolute;
    top: 0.3rem;
    left: 0.3rem;
    font-size: 1vw;
  }

  .fileLabels{
    font-weight: 700;
    position: absolute;
    bottom: 0.3rem;
    right: 0.3rem;
    font-size: 1vw;
  }

  .lightLabel {
    color: var(--light-square);
  }

  .darkLabel {
    color: var(--dark-square);
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


  /* media queries for responsiveness */
  @media (max-width: 600px){
    .square {
      width: 11vw;
      height: 11vw;
    }
    .fileLabels, .rankLabels {
        font-size: 3vw;
    }
  }

  /* landscape orientation for phones */
  @media (min-width: 600px) and (max-height: 880px){
    .square {
      width: 5vh;
      height: 5vh;
    }
  }

  @media (min-width: 600px) and (min-height: 880px){
    .square {
      width: 10vw;
      height: 10vw;
    }
    .fileLabels, .rankLabels {
        font-size: 2.5vw;
    }
  }


  @media (min-width: 768px) and (min-height: 880px){
    .square {
      width: 8vw;
      height: 8vw;
    }
    .fileLabels, .rankLabels {
        font-size: 1.5vw;
    }
  }

  @media (min-width: 992px){
    .square {
      width: 6.5vw;
      height: 6.5vw;
    }
  }

  /* some really wide laptops have really short heights. Using vh might be more appropriate there */
  @media (min-width: 1200px) and (max-height: 880px){
    .square {
      width: 10vh;
      height: 10vh;
    }
  }

  /* a media query for min-width 1200px and max-height 880px here is covered by default */

  /* desktop displays */
  @media (min-width: 1920px) {
  .square {
      width: 5.5vw;
      height: 5.5vw;
    }
  }
  </style>
