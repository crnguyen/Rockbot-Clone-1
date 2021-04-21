<template>
    <div id="nowPlaying1">
        <h4>Artist: {{music.response.now_playing.artist}}</h4>
        <img :src= music.response.now_playing.artwork_small style="height:150px;width:150px" alt="">
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
}
</style>