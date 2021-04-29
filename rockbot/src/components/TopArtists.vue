<template>
<div>
    <h3>Top Artists</h3>
    <div id="artistSection">
        <div v-for="(topartist, index) in topartist" :key="index" id="topArtists">
        <div>
            <img :src= topartist.artwork_small style="height:50px;width:50px" alt="">
            {{topartist.artist}}
        </div>
    </div>
    </div>
</div>
</template>

<script>
    export default {
    data() {
    return {
      topartist: []
    }
  },
    mounted() {
    fetch("https://api.rockbot.com/v3/engage/top_artists", {
    method: "GET",
    headers: {
      Authorization: "2ab742c917f872aa88644bc8f995e03159b2"
    }
  })
    .then(res => res.json())
    .then(response => (this.topartist = response.response))
    .then(response => {
      console.log("top artist:", response);
    })
    .catch(err => {
        console.log("top artist error:", err);
    })
  }
    }
</script>

<style scoped>
img {
    border-radius: 50%;
}

#topArtists {
    display: inline-block;  
    padding: 15px;
    vertical-align: top;
}

#artistSection {
    height: 150px;
    overflow-x: scroll;
}

</style>