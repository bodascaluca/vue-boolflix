<template>
  <div class="cover">

      <div class="img-container">
          <img class="img-cover" :src="item.poster_path ? `https://image.tmdb.org/t/p/w342/${item.poster_path}` : require('../assets/img/no-image.jpg') " alt="">
      </div>
     

      <div class="information">
          <h1>{{ item.title}}</h1>
          <h2>{{ item.original_title}}</h2>
          <img class="img-flag" v-if="hasimage(item)" :src="require(`../assets/img/` + item.original_language + `.jpg`)" alt=""/>
          <p v-else> {{ item.original_language}}</p>
          <h4>{{ item.vote_average}}</h4>

          <ul class="stars">
              <li v-for="star, index in fammivederelestelle(item.vote_average)" :key="index">&#9733;</li>
          </ul>
          <p class="paragrafo">{{item.overview}}</p>
      </div>

             <!-- <ul class="stars">
                <li v-for="star, index in fammivederelestelle(item.vote_average)" :key="index">&#9733;</li>
            </ul> -->

             <!-- <ul class="stars">
                <li v-for="star, index in Math.ceil(item.vote_average / 2)" :key="index">&#9733;</li>
            </ul> -->
            
  </div>
</template>

<script>
export default {
    name:"ContentCards",
    data:function(){
        return {
            numerostelle:"",
        }
    },
    props:{
        item:Object
    },
    methods: {
     hasimage(item) {
         //
         if (item.original_language == `en` || item.original_language == `it` ||item.original_language == `pt` || item.original_language == `fr` ) {
             return true;
         }
         else {
             return false;
         }
     },
     fammivederelestelle(vote){
         return Math.ceil(vote / 2);
     }

    //     fammivederelestelle(vote){
    //      return Math.ceil(vote / 2);
    //  }
    },
}
</script>

<style scoped lang="scss">
@import "../style/common.scss";

     .cover{
        position: relative;
        width: 250px;
        border: 1px solid yellow;
        background-color: black;
        height: 100%;
        overflow: hidden;
        overflow-y: auto;

       
        .information{
            display:none;
            color:white;
            text-align: center;
            // position: absolute;
            // left:50%;
            // top:50%;
            // transform: translate( - 50% , - 50% );
            margin: 20px;
            // margin-bottom: 0px;
            // vertical-align: top;

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
        .stars{
            display: flex;
            list-style: none;

             & li {
            color: orange;
            margin: 5px;
            }
        }  

      
    }

//   .paragrafo{
//             width: 200px;
//         }

        .cover:hover .information{
            display:block;
        }
         .cover:hover .img-container{
            display:none;
        }

        
</style>