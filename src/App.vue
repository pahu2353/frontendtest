<template>
  <img src="./assets/darkLogo.png" id="logo">
  <ChessBoard/>
  <SideBar />
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
  --dark-square: #739552;
  --light-square: #EBECD0;
  --highlight: #ffff33;

  /* to handle requirements 2 and 3, responsive positioning */
  display: flex;
  flex-direction: row;
}
#logo{
  /* preliminary css styling for the logo */
  margin-top: 10px;
  margin-left: 10px;
  width: 10%;
  height: 10%;
}

</style>
