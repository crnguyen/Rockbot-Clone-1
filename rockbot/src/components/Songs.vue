<template>
<div>
<h1>songs</h1>
<NowPlaying/>
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
</style>

