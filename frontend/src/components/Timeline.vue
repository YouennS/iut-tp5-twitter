<template>
  <div class="timeline">
    <ul>
      <li v-for="tweet in tweets">
        {{ tweet.auteur }} : {{ tweet.contenu }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'timeline',
  data () {
    return {
      tweets: [
      {auteur: 'michel', contenu: 'tweet 1'},
      {auteur: 'johndoe', contenu: 'tweet 2'},
      {auteur: 'brunomars', contenu: 'tweet 3'},
      {auteur: 'jeancapelle', contenu: 'tweet 4'}
      ]
    }
  }
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
