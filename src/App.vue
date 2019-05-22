<template>
  <div id="background">
  <div id="app">
    <h1> Welcome </h1> 
    <p id="welcome"> to NY Times most viewed articles </p> 

    <div v-if="articles!=[]"> 
      <Article v-bind:articles="articles" v-bind:articleIndex="index"/>
    </div>
    <div v-else>
      <h6> Sorry, no articles fetched. </h6>
    </div>
    
    <button id="prev" @click="previous()"> prev </button>
    <button id="next" @click="next()"> next </button>
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

button {
  background-color: rgba(0, 0, 0, 0.3);
  color: rgba(255, 255, 255, 0.7);
  border-color: rgba(0, 0, 0, 0);
  border-width: 1px;
  margin: 10px;
  width: 70px;
  height: 70px;
  border-radius: 50px;
  transition: 2s ease-out;
  bottom: 15px;
  font-size: 10px;
}

#prev {
  position: fixed;
  text-align: right;
  left: -40px;
}

#next {
  position: fixed;
  text-align: left;
  right: -40px;
}

button:hover {
  /*background: rgba(255, 255, 255, 0.3);
  color: rgba(255, 255, 255, 1);*/
  background: rgba(0, 0, 0, 0.3);
  border-color: rgba(255, 255, 255, 0.4);
  border-style: solid;
  transition: 1s ease-in;
  cursor: pointer;
}

@media screen and (max-height: 540px) {
    button {
    }
}
</style>
