<template>
  <div id="app">
    <input type="text" v-model="text" @keyup="information" placeholder="Type your keyword">
    <div v-for="post in posts" :key="post.Title">
        <p class="res"> {{ post.Title }} , {{ post.Year }} </p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default{
  name: "app",
  setup() {
    return{
    }
  },
  data() {
    return {
      text: '',
      posts : null,
    }
  },
  methods:{
    information,
  }
};
function information() {
    let searchQuery = this.text;
    const url = `https://www.omdbapi.com/?s=${searchQuery}&page=2&apikey=4c1da51e`
    axios
      .get(url)
      .then((response) => {
        this.posts = response.data.Search;
        response.data.Search = response;
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
.res{
  width: 500px;
  height: 30px;
  margin-left: auto;
  margin-right: auto;
  color: black;
  font-size: 20px;
  background-color: rgb(238, 144, 218);
}
</style>