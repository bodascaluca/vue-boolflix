<template>
  <div id="app">

     <div class="header">
      <HeaderTop 
      @recivedfilms="savefilmsArray($event)"
      @recivedserietvs="saveserietvsArray($event)"
      />
    </div>

    <div class="main">
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
    savefilmsArray(films) {
      this.films = films;
      console.log(this.films)
    },
    saveserietvsArray(serietvs) {
      this.serietvs = serietvs;
      console.log(this.serietvs)
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
  }
}
</script>

<style lang="scss">
@import "./style/common.scss";

.header{
  height:70px;
}

.main{
  background-color: grey;
  height:100%;
}

</style>
