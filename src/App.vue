<template>
  <div id="background">
  <div id="app">
    <h1> Welcome </h1> 
    <p id="welcome"> to NY Times most viewed articles </p> 

    <div v-if="articles!=[]"> 
      <Article v-bind:articles="articles" v-bind:articleIndex="index" v-on:next="next()" v-on:previous="previous()"/>
    </div>
    <div v-else>
      <h6> Sorry, no articles fetched. </h6>
    </div>
  </div>
  </div>
</template>

<script>
import Article from './components/Article.vue';
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Article
  },
  data() {
    return {
      index: 0,
      articles: [],
      errors: []
    }
  },
  mounted() {
    axios.get("https://api.nytimes.com/svc/mostpopular/v2/viewed/7.json?api-key=pPAgGA1VOUKtKDeBbG7LYE7Yro5xKSJU")
      .then(response => {
        this.articles = response.data.results;
      });
  },
  methods: {
    next() {
      this.index++;
    },
    previous() {
      this.index--;
    }
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Dawning+of+a+New+Day|Bitter&display=swap");

body {
  background-image: url(./assets/IMG_0803-1.png);
  background-size: 100vw 100vh;
}

h1 {
  margin-top: 0px;
  font-size: 3em;
  font-family: "Dawning of a New Day";
}

#welcome {
  font-family: "Bitter";
  margin-top: -40px;
  font-weight: 100;
  font-size: 12px;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  display: flex;
  flex-direction: column;
  align-items: center;
}

#background {
  position: fixed;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 100, 0.6);
  width: 100%;
  height: 100%;
}

@media screen and (min-width: 500px) {
  h1 {
    margin-top: 5vh;
  }
  #welcome {
    margin-bottom: 5vh;
  }
}
</style>
