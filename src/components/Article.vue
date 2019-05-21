<template>
  <div class="article">
    <img :src="articles[articleIndex].media[0]['media-metadata'][2]['url']" >
    <div class="content">
      <p>{{ articles[articleIndex].title }}</p>
      <p> {{ articles[articleIndex].abstract }} </p>
      <p> {{ articles[articleIndex].section }} </p>
      <a :href="articles[articleIndex]['url']" target="_blanc"> read more </a>
    </div>
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
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.content {
  position: relative;
  background-color: rgba(0, 0, 0, 0.5);
  width: 50vw;
  height: 50vh;
  box-shadow: 0px 0px 100px -50px rgb(160, 144, 144);
  color: white;
  
}
</style>
