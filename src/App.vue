<template>
  <div id="app">
    <div id="logo">
      <img src="./assets/darkLogo.png">
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

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  
  /* theme colours: inspired by chess.com (inspect element -> stylesheet) */
  --background-colour: #302E2B;
  --dark-square: #739552;
  --light-square: #EBECD0;
  --highlight: #ffff33;
  --sidebar-header: #666564;
  --sidebar-background: #ffffff;
}

#container{
  /* to handle requirements 2 and 3, responsive positioning */
  display: flex;
  flex-direction: row;
}

#logo{
  /* preliminary css styling for the logo */
  padding: 10px;
}

#logo img {

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
