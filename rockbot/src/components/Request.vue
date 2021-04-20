<template>
    <div id="request">
        <h1>This is the Request component</h1>
    </div>
    
</template

<script>
new Vue({
  el: '#request',
  data () {
    return {
      info: null
    }
  },
  mounted () {
    fetch("https://api.rockbot.com/v3/engage/now_playing", {
    method: "GET",
    headers: {
      Authorization: "2ab742c917f872aa88644bc8f995e03159b2"
    }
  })
    .then(res => res.json())
    .then(response => {
      console.log(response);
    });
  }
})


</script>

<style>

</style>
