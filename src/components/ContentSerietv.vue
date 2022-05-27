<template>
  <div class="cover">

    <div class="img-container">
        <img class="img-cover" :src="serietv.poster_path ? `https://image.tmdb.org/t/p/w342/${serietv.poster_path}` : require('../assets/img/no-image.jpg') " alt="">
    </div>

    <div class="information">
        <h1> {{ serietv.name}}</h1>
        <h2>{{ serietv.original_name}}</h2>
        <img class="img-flag" v-if="hasimage(serietv)" :src="require(`../assets/img/` + serietv.original_language + `.jpg`)" alt=""/>
        <p v-else> {{ serietv.original_language}}</p>
        <h4>{{ serietv.vote_average}}</h4>

        <ul class="stars">
            <li v-for="stelle, index in fammivederelestelle(serietv)" :key="index">&#9733;</li>
        </ul>
        <p class="paragrafo">{{serietv.overview}}</p>
    </div>

  </div>
</template>

<script>
export default {
    name:"ContentSerietv",
    props:{
        serietv:Object
    },
     methods: {
        hasimage(serietv) {
            //
            if (serietv.original_language == `en` || serietv.original_language == `it` ||serietv.original_language == `pt` || serietv.original_language == `fr` ) {
                return true;
            }
            else {
                return false;
            }
        },
        fammivederelestelle(serietv){
            console.log(serietv)
            return Math.ceil(serietv.vote_average / 2 )
        }
    },
}
</script>

<style scoped lang="scss">
@import "../style/common.scss";

 .cover{
        position: relative;
        width: 250px;
        // border: 1px solid yellow;
        background-color: black;
        height: 100%;
        overflow: hidden;
        overflow-y: auto;
 
   .information{
            display:none;
            color:white;
            text-align: center;
            margin: 20px;

            .img-flag{
                width: 20px;
            }
        }

         .img-container{
            width: 250px;
            height: 100%;

            .img-cover{
                width:100%;
                height: 100%;
            }
        }

// h1{
//     color:red;
// }

.stars{
        display: flex;
        list-style: none;

     & li {
        color: orange;
        margin: 5px;
        }
    }
 }
  .cover:hover .information{
            display:block;
        }
     .cover:hover .img-container{
        display:none;
    }
</style>