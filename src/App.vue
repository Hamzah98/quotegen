<template>
  <div id="app">
    <div id = "container">
      <div id = "text">
  <p id = "quote" class = "ani">{{QuotesArr[num].Quote}}</p>
  <p id = "author" class = "ani">{{QuotesArr[num].Author}}</p>
  </div>
  <button id = "random" v-on:click = "Random()">New Quote</button>
  </div>
  </div>
</template>

<script>
import json from './assets/quotes.json';
export default {
  name: 'app',
  data(){
    return{
      QuotesArr:[...json],
      num:0
    }
  },
  methods:{
    QuotesAr(){
      this.QuotesArr = this.QuotesArr.map((x) => {return {Quote:x.Quote,Author:x.Author}})
    },
    Random(){
      this.num = Math.floor(Math.random()*this.QuotesArr.length)
      document.getElementById('quote').classList.remove("ani");
      document.getElementById('author').classList.add("ani");
    }
  },
  beforeMount(){
    this.QuotesAr()
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  transition:0.2s ease-in-out;
}
#text{
  background-color: white;
  padding:2rem;
  margin:2rem;
}
#quote,#author{
  animation: 1s ease-out 0s 1 slideInFromLeft;
  
}
#quote{
  font-size:24px;
  font-weight:bold;
  width:auto;
 
  height:100px;
}
#author{
  font-size:20px;
  padding:4px;
}
#random{
  text-align:center;
  background-color:limegreen;
  padding:15px;
  border:none;
  outline:none;
  border-radius:6px;
  transition:0.2s ease;
}
#random:hover{
 color:white;
}
@keyframes slideInFromLeft {
  0% {
    opacity:0;
  }
  100% {
    opacity: 1;
  }
}
#container{
  padding:15px;
  background-color:aqua;
max-width:800px;
height:auto;
margin:auto;
}
</style>
