<template>
  <div id="app">

    <input type="text" placeholder="cerca film" v-model="searchWords">
    <button @click="searchFilms()">Cerca</button>

    <FilmCards :films="films"/>

  </div>
</template>

<script>
import FilmCards from "./components/FilmCards.vue" ;
import axios from 'axios';

export default {
  name: 'App',
  components:{
    FilmCards,
  },
  data(){
    return {
      films:[],
      searchWords:"",
      filtrato:[],
    }
  },
  methods:{
    searchFilms(){
       axios.get('https://api.themoviedb.org/3/search/movie?api_key=e1cde3e49c4b61eacdb30a0c144e677b&query=' + this.searchWords)
    .then((resp)=>{
      console.log(resp);
      this.films=resp.data.results;
      console.log(this.films);
    })
    }
  },
}
</script>

<style lang="scss">
@import "./style/common.scss"


</style>
