<template>
  <div id="app">

     <div>
      <HeaderTop 
      @recivedfilms="savefilmsArray($event)"
      @recivedserietvs="saveserietvsArray($event)"
      />
    </div>

    <div class="color">
      <FilmCards :films="films" :serietvs="serietvs" />
    </div>

  </div>
</template>

<script>
import FilmCards from "./components/FilmCards.vue";
import HeaderTop from "./components/HeaderTop.vue";

export default {
  name: 'App',
  methods:{
    savefilmsArray(searchwords){
      this.films=searchwords;
    },
    saveserietvsArray(searchwords){
      this.serietvs=searchwords;
    },
  },
  data: function(){
    return {
      films:[],
      serietvs:[],
    }
  },
  components:{
    FilmCards,
    HeaderTop,
  },
 
}
</script>

<style lang="scss">
@import "./style/common.scss";



</style>
