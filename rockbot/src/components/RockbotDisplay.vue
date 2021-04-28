<template>
  <div class="mainDisplay">
    <!-- this displays the "Mini Rockbot title" -->
    <div class="titleDisplay">
      {{ msg }}
    </div>

    <component :is="current"></component>
    
    <h3>Coming Up</h3>
    <!-- this is where the Queue component renders -->
    <Queue/>

    <div class="bottomTab" id="bottomTab">
        <button 
        class="grid-child nowPlayingTab"
        @click="current= 'nowPlaying','Queue'">
        Now Playing</button>
      <!-- if you click on Now Playing tab, render the Now Playing component -->
        <button
        class="grid-child requestTab"
        @click="current= 'Request'">
        Request</button>
      <!-- if you click on Request tab, render the Request component -->
    </div>
  </div>
</template>

<script>
import NowPlaying from './NowPlaying.vue'
import Queue from './Queue.vue'
import Request from './Request.vue'

// const nowPlaying ={
//   template:"<NowPlaying/>"
// }

// const request ={
//   template:"<Request/>"
// }

export default {
  name: 'RockbotDisplay',
  props: {
    msg: String
  },
  components: {
    NowPlaying,
    Queue,
    Request
  },
  data(){
    return {
      current: ["NowPlaying", "Queue"]
    }
  },
  methods: {
      nowPlay: function() {
        console.log("you clicked the now playing tab");
        //show the now NowPlaying component, hide the Request component
      },
      req: function() {
        console.log("clicked Request tab");
        //show the Request component and hide the NowPlaying component
      }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 20px 0 0 0;
  font-weight: bold;
  text-decoration: underline;
  letter-spacing: 3;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  padding-bottom: 10px;
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
  width: 60%;
  margin: auto;
  box-shadow: 5px 9px #888888;
}

.titleDisplay {
  background-color: #017EE4;
  color: white;
  font-size: 25px;
  letter-spacing: 5;
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
