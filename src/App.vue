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

// #app{
//   background-color: grey;
// }


.header{
  height:70px;
  width:100%;
  position: fixed;
  top:0;
  left:0;
}

.main{
  background-color: grey;
  margin-top:70px;
  padding-left:2rem;
}

</style>
