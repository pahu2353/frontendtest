<template>
  <div id="app">
    <div class="logo">
      <img src="./assets/lightLogo.png">
    </div>
  <div id="container">
    <ChessBoard/>
    <SideBar />
  </div>
</div>
</template>

<script>
import ChessBoard from './components/ChessBoard.vue';
import SideBar from './components/SideBar.vue';

export default {
  name: 'App',
  components: {
    ChessBoard,
    SideBar
  }
}

</script>

<style>
body {
  /* allow #app to fill entire viewport */
  margin: 0;
  padding: 0;
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
  margin: 1.5rem 2rem 2rem; /* top, right, left */
  display: flex;
  justify-content: center;
  flex-direction: row;
  gap: 2rem;
}

.logo{
  /* preliminary css styling for the logo */
  padding: 1.5rem 2rem 0; 
}

.logo img {
  /* temporary values, to be changed later */
  width: 183.4px;
  height: 50.8px;
}

/* breakpoint for switching sidebar to below, inspired by https://www.chess.com/analysis */
@media (max-width: 960px) {
  #app {
    flex-direction: column;
  }
}

</style>
