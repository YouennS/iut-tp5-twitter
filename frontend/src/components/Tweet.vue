<template>
  <div class="tweet">
    <div>
      <strong>{{tweet.auteur.prenom}} {{tweet.auteur.nom}}</strong>
      <span class=handle>@{{tweet.auteur.handle}}</span>
      -- {{moment()}}
    </div>
    <div>
      {{tweet.contenu}}
    </div>
    <div>
      <ul>
        <li class=button>
          <icon name="reply"/>
        </li>
        <li class=button>
          <a @click="retweet(tweet.id)">
            <icon name="retweet"/>
          </a>
          {{tweet.retweeters.length}}
        </li>
        <li class=button>
          <icon name="heart"/>
        </li>
        <li class=button>
          <icon name="envelope"/>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import 'vue-awesome/icons'
import Icon from 'vue-awesome/components/Icon'
import moment from 'moment'
import Vue from 'vue'
import Resource from 'vue-resource'
Vue.use(Resource)

export default {
  created () {
    moment.locale('fr')
  },
  name: 'tweet',
  props: ['tweet'],
  components: {Icon},
  methods: {
    moment: function () {
      return moment(this.tweet.date).fromNow()
    },
    retweet: function (tweetId) {
      this.$http.get('http://localhost:8080/retweet', {
        responseType: 'text',
        params: {
          utilisateur: 'johndoe',
          tweet: this.tweet.id
        }
      }, resp => {
        
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li.button {
 display: inline-block;
}

a {
 color: #42b983;
}

span.handle {
 color: gray;
}
</style>
