<template>
  <div id="wrapper">
  <div class="article">
    <div class="crop">
      <img :src="articles[articleIndex].media[0]['media-metadata'][2]['url']" >
    </div>
    <div class="content">
      <div>
        <p id="section"> {{ articles[articleIndex].published_date }} </p>
        <p id="section"> {{ articles[articleIndex].section }} </p>
      </div>
      <div class="text">
        <p id="header">{{ articles[articleIndex].title }}</p>
        <p id="description"> {{ articles[articleIndex].abstract }} </p>
      </div>
    </div>
  </div>
    <div id="buttons">
      <button id="prev" @click="previous()"> prev </button>
      <button id="readMore">
      <a :href="articles[articleIndex]['url']" target="_blanc"> read more </a>
      </button>
      <button id="next" @click="next()"> next </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Article',
  props: {
    articleIndex: Number,
    articles: Array
  },
  methods: {
    next() {
      this.$emit("next");
    },
    previous() {
      this.$emit("previous");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Dawning+of+a+New+Day|Bitter&display=swap");

.article {
  background-color: rgba(0, 0, 0, 0.3);
}
#description {
  padding: 0 20px 0 20px;  
}
#header {
  font-family: "Bitter";
  padding: 0 20px 0 20px;
}
.text {
  margin-right: 15px;
}
.content {
  display: flex;
  flex-direction: row;
  justify-content: left;
  width: 100%;
  height: 800px;
  color: white;
  margin: -5px;
  padding: 20px;
}
p {
  font-size: 10px;
  text-align: left;
}
#section {
  color: rgba(255, 255, 255, 0.3);
}
a {
  color: white;
  text-decoration: none;
  font-family: Bitter;
}
#readMore {
  position: fixed;
  left: 50;
  margin-left: -35px;
  bottom: 5px;
  border-color: white;
  border-style: solid;
  border-width: 0.5px;
}
.crop {
    height: 25vh; 
    overflow: hidden;
}

img {
  width: 100vw;
  object-fit: cover;
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
  bottom: 5px;
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

@media screen and (min-height: 600px) {
    .crop {
      height: auto;
    }
    #next, #prev, #readMore {
      bottom: 25px;
    }
}

@media screen and (min-width: 500px) {
    .crop {
      height: 30vh;
      width: 400px;
    }
    img {
      width: 400px;
      object-fit: cover;
      border-radius: 10px 10px 0 0;
    }
    .article {
      display: flex;
      justify-content: center;
      flex-direction: column;
      border-radius: 10px;
      padding-bottom: 20px;
    }
    .content {
      width: 300px;
      height: 100%;
      margin: auto;
      padding: 20px 0 0 0;
    }
    #header, #description {
      padding:  0 0 0 20px;
    }
  
  #buttons {
    display: flex;
    justify-content: center;
    flex-direction: row;
  }
  
  #prev, #next, #readMore {
    position: relative;
    top: 10px;
    text-align: center;
    left: 0;
    right: 0;
    margin: 10px;
  }
}

</style>
