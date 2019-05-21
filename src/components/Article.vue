<template>
  <div class="article">
    <p>{{ articles[articleIndex].title }}</p>
    <p> {{ articles[articleIndex].abstract }} </p>
    <p> {{ articles[articleIndex].section }} </p>
    <a :href="articles[articleIndex]['url']" target="_blanc"> read more </a>
    </br>
    <img :src="articles[articleIndex].media[0]['media-metadata'][2]['url']" >
    
  </div>
</template>

<script>
export default {
  name: 'Article',
  props: {
    articleIndex: Number,
    articles: Array
  },
  data() {
    return {
      img: ""
    }
  },
  methods: {
    getImg(index) {
      this.img = articles[index].media[0][2];
    }
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
.article {
  position: relative;
  background-color: rgba(2300, 255, 255, 0.8);
  width: 50vw;
  height: 50vh;
  box-shadow: 0px 0px 100px -50px rgba(255,255,255,1);
  color: rgb(10, 10, 10);
}
</style>
