<template>
  <div id="background">
  <div id="app">
    <h1> Welcome </h1> 
    <h3> to NY Times most viewed articles </h3> 

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
    console.log("mounted"),
    axios.get("https://api.nytimes.com/svc/mostpopular/v2/viewed/7.json?api-key=pPAgGA1VOUKtKDeBbG7LYE7Yro5xKSJU")
      .then(response => {
        this.articles = response.data.results;
        console.log(response.data.results);
      });
  },
  methods: {
    next() {
      this.index++;
      console.log('cur index: ', this.index);
    },
    previous() {
      this.index--;
      console.log('cur index: ', this.index);
    }
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Dawning+of+a+New+Day&display=swap");

body {
  background-image: url(./assets/IMG_0803-1.png);
  background-size: 100vw 100vh;
}

h1 {
  font-size: 4.6em;
}

h3 {
  margin-top: -1em;
  font-family: "Dawning of a New Day";
  font-size: 2em;
  font-weight: 100;
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
  background-color: transparent;
  color: rgba(255, 255, 255, 0.7);;
  border-style: solid;
  border-width: 1px;
  border-color: rgba(255, 255, 255, 0.4);
  margin: 10px;
  width: 150px;
  height: 150px;
  border-radius: 100px;
  transition: 2s ease-out;
  top: 50vh;
}

#prev {
  position: fixed;
  text-align: right;
  left: -100px;
}

#next {
  position: fixed;
  text-align: left;
  right: -100px;
}

button:hover {
  /*background: rgba(255, 255, 255, 0.3);
  color: rgba(255, 255, 255, 1);*/
  background: rgba(0, 0, 0, 0.3);
  border-color: rgba(0, 0, 0, 0);
  transition: 1s ease-in;
  cursor: pointer;
}
</style>
