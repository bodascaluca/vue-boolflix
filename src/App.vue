<template>
  <div id="app">
    <div class="header">
      <div class="header-left">
        <img class="img-luflix" src="./assets/img/luflix.png" alt="">
      </div>
      <div class="header-right">
        <input type="text" placeholder="cerca film" v-model="searchWords">
        <button @click="searchFilms()">Cerca</button>
      </div>
    </div>

    <div class="color">
      <FilmCards :films="films" :serietvs="serietvs" />
    </div>

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
      serietvs:[]
    }
  },
  methods:{
    searchFilms(){


       axios
       .get('https://api.themoviedb.org/3/search/movie', {
         params:{
           api_key:"e1cde3e49c4b61eacdb30a0c144e677b",
           query:this.searchWords,
         }
       })
        //  .get(`https://api.themoviedb.org/3/search/movie?api_key=e1cde3e49c4b61eacdb30a0c144e677b&api_key=e99307154c6dfb0b4750f6603256716d&query=`+ this.searchWords)
    .then((resp)=>{
      this.films=resp.data.results;
    })




        axios
      .get(`https://api.themoviedb.org/3/search/tv`,{
        params:{
          api_key:"e99307154c6dfb0b4750f6603256716d",
          query:this.searchWords,
        }
      })
   
    .then((resp)=>{
      this.serietvs=resp.data.results;
    })
    }
  },
}
</script>

<style lang="scss">
@import "./style/common.scss";

#app{
  height:100vh;
  background: linear-gradient(to bottom,  black 0vh,
                                          black 15vh,
                                          grey 15vh,
                                          grey 100%);
}

  .header{
    display: flex;
    align-items: center;
    justify-content: space-between;

    &-left{
      margin-left:1rem;

      .img-luflix{
          width: 200px;
      }
    }

    &-right{
      margin-right:1rem;
    }
  }


</style>
