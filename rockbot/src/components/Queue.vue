<template>
    <!-- this component should include now playing data from API 
    and the Queue component below it -->
    <div id="Queue">
        <div v-for="(music, index) in music" :key="index" id="queueInfo">
            <img :src= music.artwork_small style="height:50px;width:50px" alt="">
            <div id="artistInfo">
                <h6>Artist: {{music.artist}}</h6>
                <h6>Song: {{music.song}}</h6>
            </div>
            <div id="counterInfo">
                <mdb-icon @click.native="like" icon="plus-circle"/>
                <h6>Likes: {{counter}}</h6>
            </div>
            <hr/>
        </div>
    </div>
</template>

<script>
import { mdbIcon } from 'mdbvue';
export default {
    components: {
    mdbIcon
  },
  methods: {
      like: function() {
          console.log("you clicked the icon");
          this.counter += 1
      }
  },
//   el: '#nowPlaying1', el only needed during new vue instance creation
  data() {
    return {
      music: [],
      counter: 0,
    }
  },
  mounted() {
    fetch("https://api.rockbot.com/v3/engage/now_playing?queue=1", {
    method: "GET",
    headers: {
      Authorization: process.env.VUE_APP_ROCKBOT_KEY
    }
  })
    .then(res => res.json())
    .then(response => (this.music = response.response.queue))
    //response.response.queue[0] = first song/artist in queue
    //loop through queue and display the artist and small artwork
    //include button to like the artist
    .then(response => {
      console.log(response);
    })
    .catch(err => {
        console.log(err);
    })
  }
}
</script>

<style scoped>
#Queue {
    text-align: left;
    padding: 0px 30px 15px 30px;
    height: 150px;
    overflow-x: scroll;
}

img {
    border-radius: 50%;
}

#queueInfo {
    display: grid;
    grid-template-columns: 1fr 6fr 2fr;
}

#artistInfo {
    padding-left: 5px;
}

hr {
    height: 5px;
    background-color: #d3d3d3;
}
</style>