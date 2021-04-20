<template>
  <div class="mainDisplay">
    <!-- this displays the "Mini Rockbot title" -->
    <div class="titleDisplay">
      {{ msg }}
    </div>

    <h3>Now Playing</h3>
    <!-- this is where the NowPlaying component renders -->
    {{music}}
    <NowPlaying/>
    
    <h3>Coming Up</h3>
    <!-- this is where the Queue component renders -->
    <Queue/>

    <div class="bottomTab" id="bottomTab">
        <button class="grid-child nowPlayingTab">Now Playing</button>
      <!-- if you click on Now Playing tab, render the Now Playing component -->
        <button class="grid-child requestTab">Request</button>
      <!-- if you click on Request tab, render the Request component -->
    </div>
  </div>
</template>

<script>
// import Vue from 'vue'
import NowPlaying from './NowPlaying.vue'
import Queue from './Queue.vue'

export default {
  name: 'RockbotDisplay',
  props: {
    msg: String
  },
  components: {
    NowPlaying,
    Queue
  },
}
    
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.mainDisplay {
  border: black solid 2px;
  width: 80%;
  margin: auto;
}

.titleDisplay {
  background-color: #017EE4;
  color: white;
  padding-top: 0px;
  font-size: 25px;
  font-weight: bold;
  border-bottom: black solid 2px;
}

.bottomTab {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.nowPlayingTab {
  border-top: black solid 2px;
  border-right: black solid 1px;
  height: 50px;
  /* border-bottom: black solid 2px; */
}

.requestTab {
  border-top: black solid 2px;
  border-left: black solid 1px;
  height: 50px;

  /* border-bottom: black solid 2px; */
}

</style>
