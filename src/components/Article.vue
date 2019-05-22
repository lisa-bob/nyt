<template>
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
    <button>
      <a :href="articles[articleIndex]['url']" target="_blanc"> read more </a>
    </button>
  </div>
</template>

<script>
export default {
  name: 'Article',
  props: {
    articleIndex: Number,
    articles: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Dawning+of+a+New+Day|Bitter&display=swap");

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
  background-color: rgba(0, 0, 0, 0.3);
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
button {
  position: fixed;
  left: 50;
  margin-left: -35px;
  bottom: 20px;
  border-color: white;
  border-style: solid;
  border-width: 0.5px;
}
.crop {
    height: auto; 
    overflow: hidden;
}

img {
  width: 100vw;
  object-fit: cover;
}

@media screen and (max-height: 540px) {
    .crop {
      height: 200px;
    }
}
</style>
