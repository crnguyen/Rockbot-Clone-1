<template>
    <div id="nowPlaying">
        <img :src= music.response.now_playing.artwork_small style="height:130px;width:130px" alt="">
        <div id="artistInfo">
            <p><b>{{music.response.now_playing.artist}}</b></p>
            <p>{{music.response.now_playing.song}}</p>  
        </div>   
    </div>
</template>

<script>
export default {
//   el: '#nowPlaying1', el only needed during new vue instance creation
  data() {
    return {
      music: null
    }
  },
  mounted() {
    fetch("https://api.rockbot.com/v3/engage/now_playing", {
    method: "GET",
    headers: {
      Authorization: "2ab742c917f872aa88644bc8f995e03159b2"
    }
  })
    .then(res => res.json())
    .then(response => (this.music = response))
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
img {
  border-radius: 50%;
  padding: 10px;
}

#nowPlaying {
    text-align: left;
    padding-left: 15px;
    display: flex;
    align-items: center;
}

#artistInfo {
    max-height: 130px;
    line-height: 110%;
    padding-left: 10px;
    padding-right: 10px;
}

p {
    font-size: 20px;
    /* font-size: 2vw; */
}

b {
    font-weight: bold;
}
</style>