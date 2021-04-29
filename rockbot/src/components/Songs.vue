<template>
<div>
<h3>Now Playing</h3>
<NowPlaying/>

<h3>Up Next</h3>
<Queue/>
</div>

</template>

<script>
import NowPlaying from './NowPlaying.vue'
import Queue from './Queue.vue'

export default {
components: {
    NowPlaying,
    Queue,
  },
}
</script>

<style>
h3 {
  margin: 20px 0 0 0;
  font-weight: bold;
  text-decoration: underline;
  text-align: left;
  letter-spacing: 3;
  /* font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; */
  padding-bottom: 10px;
  padding-left: 20px;
  padding-top: 20px;
}
</style>

