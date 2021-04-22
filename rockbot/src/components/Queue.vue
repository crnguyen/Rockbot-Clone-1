<template>
    <!-- this component should include now playing data from API 
    and the Queue component below it -->
    <div id="Queue">
        <div v-for="(music, index) in music" :key="index">
            <h6>Artist: {{music.artist}}</h6>
            <h6>Song: {{music.song}}</h6>
            <mdb-icon @click.native="like" icon="plus-circle"/>
            <h6>Likes: {{music.likes}} + {{ counter }}</h6>
            <img :src= music.artwork_small style="height:50px;width:50px" alt="">
            <hr/>
        </div>
    </div>
</template>

<script>
import { mdbIcon } from 'mdbvue';
let object = {
  counter: 0
}
export default {
    components: {
    mdbIcon
  },
  methods: {
      like: function() {
          console.log("you clicked the icon");
          this.counter += 1;
      }
  },
//   el: '#nowPlaying1', el only needed during new vue instance creation
  data() {
    return {
      music: [],
      object,
    }
  },
  mounted() {
    fetch("https://api.rockbot.com/v3/engage/now_playing?queue=1", {
    method: "GET",
    headers: {
      Authorization: "2ab742c917f872aa88644bc8f995e03159b2"
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
    /* padding-left: 30px;
    padding-bottom: 15px; */
    padding: 0px 30px 15px 30px;
    height: 150px;
    overflow-x: scroll;
}

img {
    border-radius: 50%;
}

hr {
    height: 5px;
    background-color: #d3d3d3;
}
</style>