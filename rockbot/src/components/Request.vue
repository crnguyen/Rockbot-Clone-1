<template>
    <div id="request">
        <TopArtist/>
        <h3>Search</h3>
        <div class="searchBar">
            <input type="text" aria-label="Search" v-model="search" placeholder="Search artist">
        </div> 
        <button
        id="submitButton"
        type="submit"
        v-on:click="getData">Submit
        </button>

        <div id="searchArtistResults">
            <div v-for="(artist, index) in artist" :key="index" id="artistInfo">
            {{artist.artist}}
            <button id="addToQueueButton" @click="addToQueue">Add to Queue</button>
            </div>
        </div>
    </div>
</template>

<script>
    import TopArtist from "./TopArtists"
    export default {
    //   el: '#nowPlaying1', el only needed during new vue instance creation
    components: {
        TopArtist
    },
    data() {
        return {
        artist: [],
        search: ""
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
        },
        addToQueue: function(){
            console.log("this is supposed to add artist to up next section")
        }
    }
}
</script>

<style scoped>
    #request {
        display: block;
    }

    input {
        width: 200px;
        padding-left: 20px;
    }

    #artistInfo {
        padding: 5px;
    }

    #searchArtistResults {
        height: 100px;
        overflow-x: scroll;
        text-align: left;
        padding-left: 15px;
    }

    #addToQueueButton {
        width: 90px;
        font-size: 11px;
        background-color: #1865AA;
        color: white;
        border-radius: 10px;
        border: none;
    }

    #submitButton {
        margin: 5px;
        background-color: #017EE4;
        color: white;
        border-radius: 10px;
        border: none;
    }
</style>
