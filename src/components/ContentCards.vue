<template>
  <div>
            <h1>{{ item.title}}</h1>
            <img :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" alt="">
            <h2>{{ item.original_title}}</h2>
            <img class="img-flag" v-if="hasimage(item)" :src="require(`../assets/img/` + item.original_language + `.jpg`)" alt=""/>
            <p v-else> {{ item.original_language}}</p>
            <h4>{{ item.vote_average}}</h4>

            <ul class="stars">
                <li v-for="star, index in Math.ceil(item.vote_average / 2)" :key="index">&#9733;</li>
            </ul>
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

    },
}
</script>

<style scoped lang="scss">

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