<template>
  <div>
      <img :src="`https://image.tmdb.org/t/p/w342/${serietv.poster_path}`" alt="">
        <h1> {{ serietv.name}}</h1>
        <h2>{{ serietv.original_name}}</h2>
        <img class="img-flag" v-if="hasimage(serietv)" :src="require(`../assets/img/` + serietv.original_language + `.jpg`)" alt=""/>
        <p v-else> {{ serietv.original_language}}</p>
        <h4>{{ serietv.vote_average}}</h4>
        <ul class="stars">
            <li v-for="stelle, index in fammivederelestelle(serietv)" :key="index">&#9733;</li>
        </ul>
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

h1{
    color:red;
}

.stars {
        display: flex;
        list-style: none;
    }

    .stars li {
        color: orange;
        margin: 5px;
    }
.img-flag{
        width: 20px;
    }

</style>