<template>
  <div id="app">
    <Main msg="Vue.js / Threejs template"/>
  </div>
</template>

<script>
import Main from './components/scenes/Main'

export default {
  name: 'App',
  components: {
    Main
  }
}
</script>

<style lang="scss">

/* Import des variables */
@import "./assets/variables/colors.scss";
@import "./assets/variables/spaces.scss";
@import "./assets/variables/medias.scss";
@import "./assets/variables/misc.scss";
@import "./assets/variables/reset.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
}

html::-webkit-scrollbar {
  width: 10px;
  background-color: var(--colorPrimaryVeryLight); 
}
html::-webkit-scrollbar-thumb {
  background: var(--colorPrimary); 
}

body{
  padding: 0;
  margin:0;
  transition: all 0.5s ease;
}

</style>
