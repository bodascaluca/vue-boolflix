<template>
  <div class="header">

      <div class="header-left">
        <img class="img-luflix" src="../assets/img/luflix.png" alt="">
      </div>
    
      <div class="header-right">
        <input class="header-right-input" type="text" placeholder="Cerca film o serie Tv " v-model="searchWords">
        <button class="header-right-button" @click="searchFilms()">Search</button>
      </div>

  </div>
</template>

<script>
import axios from 'axios';

export default {
    name:"HeaderTop",
     data(){
    return {
      films:[],
      searchWords:"",
      serietvs:[]
    }
  },
  methods:{
    searchFilms(){

      const options = {
        params:{
          api_key:"e99307154c6dfb0b4750f6603256716d",
          query:this.searchWords,
        }
      }

      axios.get('https://api.themoviedb.org/3/search/movie', options)
      .then((resp)=>{
        this.films = resp.data.results;
        this.$emit('recivedfilms', this.films);
      });

      axios.get(`https://api.themoviedb.org/3/search/tv`, options)
      .then((resp)=>{
        this.serietvs = resp.data.results;
        this.$emit('recivedserietvs', this.serietvs);
      });
    }
  },
}
</script>

<style scoped lang="scss">
@import "../style/common.scss";

  .header{
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: black;

    &-left{
      margin-left:2rem;

      .img-luflix{
          height: 50px;
      }
    }

    .header-right{
      margin-right:1rem;

      &-input{
        padding: .3rem .6rem;
        border-radius:10px 0 0 10px;
        background-color: white;
        border-right:none;
        border: 1px solid white ;
        color:grey;
      }

      &-button{
        padding: .3rem 1rem;
        border-radius:0 10px 10px 0;
        background-color: white;
        border-left:none;
        border: 1px solid white;
        color:grey;
      }
    }
  }
</style>