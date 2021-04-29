<template>
    <div id="request">
        <h3>Search</h3>
        <div class="searchBar">
            <input type="text" v-model="search" placeholder="Search artist">
        </div> 
        <button
        type="submit"
        v-on:click="getData">submit
        </button>

        <div v-for="(artist, index) in artist" :key="index">
            {{artist.artist}}
        </div>
    </div>
</template>

<script>
// request artist 
export default {
//   el: '#nowPlaying1', el only needed during new vue instance creation
  data() {
    return {
      artist: []
    }
  },
  methods: {
      getData: function(){
          fetch(`https://api.rockbot.com/v3/engage/search_artists?query=${this.search}`, {
              method: "GET",
              headers: {
                  Authorization: "2ab742c917f872aa88644bc8f995e03159b2"
            }
        })
        .then(res => res.json())
        .then(response => (this.artist = response.response))
        .then(response => {
            console.log("search response:", response);
        })
        .catch(err => {
            console.log("search error:", err);
        })
        }
    }
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

#request {
    display: block;
}

input {
    width: 200px;
    padding-left: 20px;
}

</style>
