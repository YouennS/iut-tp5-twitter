<template>
  <div class="timeline">
    <h1>hola</h1>
    <feed :tweets="tweets" :loading="loading" @retweeted="retweet"/>
  </div>
</template>

<script>
import Feed from './Feed'
import Vue from 'vue'
import Resource from 'vue-resource'
Vue.use(Resource)

export default {
  name: 'timeline',
  data () {
    return {
      tweets: [],
      loading: true
    }
  },
  created () {
    this.fetchTweets()
  },
  methods: {
    fetchTweets: function () {
      this.$http.get('http://localhost:8080/list').then(response => {
        this.tweets = response.body
        this.loading = false
      },
      response => {
        // error callback
      })
    },
    retweet: function (id) {
      // maj
    }
  },
  components: {Feed}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
