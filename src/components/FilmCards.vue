<template>
    <div class="flex" >
       
       <div class="card" v-for="(item, index) in films" :key="index" >
            <h1>{{ item.title}}</h1>
            <h2>{{ item.original_title}}</h2>
            <h3>{{ item.original_language}}</h3>
            <h4>{{ item.vote_average}}</h4>
        </div>
    
    </div>
</template>

<script>
export default {
    name:"FilmCards",
    props:{
        films:Array
    }
}
</script>

<style scoped lang="scss">
@import "../style/common.scss";
    
    .flex{
        display: flex; 
        flex-wrap: wrap;  
    }
    .card{
        margin:1rem;
        border:1px solid red;
        width: calc(100% / 4 - 2px);
    }

</style>