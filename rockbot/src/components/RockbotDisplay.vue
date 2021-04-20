<template>
  <div class="mainDisplay">
    <!-- this displays the "Mini Rockbot title" -->
    <div class="titleDisplay">
      {{ msg }}
    </div>

    <h3>Now Playing</h3>
    <!-- this is where the NowPlaying component renders -->
    <NowPlaying/>
    
    <h3>Coming Up</h3>
    <!-- this is where the Queue component renders -->
    <Queue/>

    <div class="bottomTab">
      <h3 class="grid-child nowPlayingTab">Now Playing</h3>
      <!-- if you click on Now Playing tab, render the Now Playing component -->
      
      <h3 v-on:click="showRequest" class="grid-child requestTab" id="request">Request</h3>
      <!-- if you click on Request tab, render the Request component -->
      <Request/>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import Request from './Request.vue'
import NowPlaying from './NowPlaying.vue'
import Queue from './Queue.vue'

export default {
  name: 'RockbotDisplay',
  props: {
    msg: String
  },
  components: {
    Request,
    NowPlaying,
    Queue
  }

}

//this API call is working
    fetch("https://api.rockbot.com/v3/engage/now_playing", {
    method: "GET",
    headers: {
      Authorization: "2ab742c917f872aa88644bc8f995e03159b2"
    }
  })
    .then(res => res.json())
    .then(response => {
      console.log(response);
    });

new Vue({
  el: '#request',
  data: {
    name: 'Vue.js'
  },
  // define methods under the `methods` object
  methods: {
    showRequest: function (event) {
      // `this` inside methods points to the Vue instance
      console.log("hi")
      // `event` is the native DOM event
      if (event) {
        alert(event.target.tagName)
      }
    }
  }
})
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
  /* grid-gap: 20px; */
}

.nowPlayingTab {
  border-top: black solid 2px;
  border-right: black solid 1px;
  /* border-bottom: black solid 2px; */
}

.requestTab {
  border-top: black solid 2px;
  border-left: black solid 1px;
  /* border-bottom: black solid 2px; */
}

</style>
