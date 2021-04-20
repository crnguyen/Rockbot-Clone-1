<template>
    <div id="nowPlaying1">
        {{music}}
        <h5>This is the now playing component</h5>
    </div>
</template>

<script>
import Vue from "vue"

export default new Vue({
  el: '#nowPlaying1',
  data() {
    return {
      music: null
    }
  },
  template: '<div id="nowPlaying1">{{ music }}</div>',
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
      console.log(response.response.now_playing.artist);
    })
    .catch(err => {
        console.log(err);
    })
  }
})
</script>

<style>
</style>