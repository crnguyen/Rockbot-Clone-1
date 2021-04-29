<template>
  <div id="app">
    <img alt="Rockbot logo" src="./assets/logo.png" height="100px">
    <Rockbot msg="Mini Rockbot"/> 

    <div id="credits">
      <p>Designed by: Cristina Nguyen</p>
      <a href="https://www.linkedin.com/in/cristinanguyen/" target="_blank" class="li-ic mr-3" role="button"><mdb-icon fab icon="linkedin-in" size="lg"/></a>
      <a href="https://github.com/crnguyen" target="_blank" class="git-ic mr-3" role="button"><mdb-icon fab icon="github" size="lg"/></a>
    </div>
    
  </div>
</template>

<script>
import Rockbot from './components/RockbotDisplay.vue'
import { mdbIcon } from 'mdbvue';

export default {
  name: 'App',
  components: {
    Rockbot,
    mdbIcon,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  min-height: 300px;
  max-height: 300px;
  /* margin-top: 60px; */
}

#credits {
  padding-top: 15px;
}

@import url('https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap');

</style>
