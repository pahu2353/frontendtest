<template>
  <div id="app">
    <div class="logo">
      <img src="./assets/noCopyrightLogo.png">
    </div>
  <div id="container">
    <ChessBoard
      @emitHistory="addHistory"
    />
    <SideBar 
      :coordinateHistory="coordinateHistory"
      :currentlyClicked="currentlyClicked"
    />
  </div>
</div>
</template>

<script setup> // script setup makes it much more concise
import ChessBoard from './components/ChessBoard.vue';
import SideBar from './components/SideBar.vue';

import { ref } from 'vue';

const coordinateHistory = ref([]);
const currentlyClicked = ref(new Set());

// adds history to coordinateHistory and also inserts/removes form the currentlyClicked set
const addHistory = (coordinate) => {
  if (currentlyClicked.value.has(coordinate)){
        currentlyClicked.value.delete(coordinate);
      } else {
        currentlyClicked.value.add(coordinate);
        coordinateHistory.value.push(coordinate); // only add it to the history if it's highlighting, not if unhighlighting
      }
}

</script>

<style>
html, body {
  /* allow #app to fill entire viewport */
  margin: 0;
  padding: 0;

  /* for fixing ios issues */
  height: 100vh;
  width: 100vw;
}

#app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-size: 1rem;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  
  /* theme colours: inspired by chess.com (inspect element -> stylesheet) */
  --background-colour: #302E2B;
  --dark-square: #739552;
  --light-square: #EBECD0;
  --highlight-dark-square: #d36c51;
  --highlight-light-square: #ec7d6a;
  --sidebar-header-background: #F1F1F1;
  --sidebar-header-text: #666564;
  --sidebar-background: #FFFFFF;

  /* sized background-color to the viewport */
  min-height: 100vh;
  min-width: 100vw;
  background-color: var(--background-colour);
}

#container{
  /* to handle requirements 2 and 3, responsive positioning */
  margin: 1.5rem 2rem 2rem 2rem; /* top, right, bottom, left */
  display: flex;
  justify-content: center;
  flex-direction: row;
  gap: 2rem;
  height: calc(100vh - 12rem);
}

.logo{
  /* preliminary css styling for the logo */
  padding: 1.5rem 2rem 0; 
}

.logo img {
  /* temporary values, could be changed later */
  width: 183.4px;
  height: 50.8px;
}

/* breakpoint for switching sidebar to below, inspired by https://www.chess.com/analysis */
@media (max-width: 960px) {
  #container {
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: calc(100vh - 8rem);
  }

  .sidebar, .chessboard {
    width: 100%;
  }
}

</style>
