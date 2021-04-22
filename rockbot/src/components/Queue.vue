<template>
    <!-- this component should include now playing data from API 
    and the Queue component below it -->
    <div id="Queue">
        <div v-for="(music, index) in music" :key="index">
            <h6>Artist: {{music.artist}}</h6>
            <h6>Song: {{music.song}}</h6>
            <mdb-icon icon="plus-circle"/>
            <h6>Likes: {{music.likes}}</h6>
            <img :src= music.artwork_small style="height:50px;width:50px" alt="">
        </div>
    </div>
</template>

<script>
import { mdbIcon } from 'mdbvue';

export default {
    components: {
    mdbIcon
  },
//   el: '#nowPlaying1', el only needed during new vue instance creation
  data() {
    return {
      music: []
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
    padding-left: 15px;
    padding-bottom: 15px;
    height: 200px;
    overflow-x: scroll;
}

img {
    border-radius: 50%;
}
</style>