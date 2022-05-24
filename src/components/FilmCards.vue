<template>
    <div class="flex" >
       
       <div class="card" v-for="(item, index) in films" :key="index" >
            <h1>{{ item.title}}</h1>
            <h2>{{ item.original_title}}</h2>
            <img class="img-flag" v-if="hasimage(item)" :src="require(`../assets/img/` + item.original_language + `.jpg`)" alt=""/>
            <p v-else> {{ item.original_language}}</p>
            <h4>{{ item.vote_average}}</h4>
        </div>
    
    </div>
</template>

<script>
export default {
    name:"FilmCards",
    props:{
        films:Array
    },
    methods:{
        hasimage(item){
            //
            if(item.original_language == `en` && `it` && `pt`){
                return true;
            } else {
                return false;
            }
        }
    }
}
</script>

<style scoped lang="scss">
@import "../style/common.scss"; 
    
    .flex{
        display: flex; 
        flex-wrap: wrap;  
    }

    .img-flag{
        width: 20px;
    }
    .card{
        margin:1rem;
        border:1px solid red;
        width: calc(100% / 4 - 2px);
    }

</style>