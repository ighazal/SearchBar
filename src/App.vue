<template>
  <div id="app">
    <input id="inp" type="text" v-model="text" @keyup="information" placeholder="Type your keyword">
    <div v-for="post in posts" :key="post.Title">
      <p> {{ post.Type }} </p>
      <!--<post_a :post="post"></post_a>-->
    </div>
  </div>
</template>

<script>
/*import post_a from './components/Post';*/
import axios from 'axios';
export default{
  name: "app",
  /*components: {post_a},*/
  setup() {
    return{
    }
  },
  data() {
    return {
      text: '',
      posts : null
    }
  },
  methods:{
    information,
  }
};
function information() {
    let searchQuery = this.text;
    console.log("here");
    console.log(searchQuery);
    const url = `https://www.omdbapi.com/?s=${searchQuery}&page=2&apikey=4c1da51e`
    axios
      .get(url)
      .then((response) => {
        this.posts = response
      })
      .catch((error) => {
        this.posts  = error
      })
    }
</script>

<style>
#app {
  text-align: center;
  color: lightslategrey;
  margin-top: 60px;
}
</style>