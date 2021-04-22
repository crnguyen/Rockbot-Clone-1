<template>
    <!-- this component should include now playing data from API 
    and the Queue component below it -->
    <div id="Queue">
        <h4>This is the queue component</h4>
        {{music.artist}}
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
    fetch("https://api.rockbot.com/v3/engage/now_playing?queue=1", {
    method: "GET",
    headers: {
      Authorization: "2ab742c917f872aa88644bc8f995e03159b2"
    }
  })
    .then(res => res.json())
    .then(response => (this.music = response.response.queue[0]))
    //loop through queue and display the artist and small artwork
    //include button to like the artist
    .then(response => {
      console.log(response.response.queue[0]);
    })
    .catch(err => {
        console.log(err);
    })
  }
}
</script>

<style>
</style>