<template>
    <div class="flex" >
    
        
        <div class="card" v-for="(item, index) in films" :key="index">
        <h2>Film</h2>
        <ContentCards :item="item"/>
    </div>


    <div class="card" v-for="(serietv) in serietvs" :key="serietv.id">
    <h2>Serie tv</h2>
        <ContentSerietv :serietv="serietv"/>
    </div>
    
    </div>
</template>

<script>
import ContentCards from './ContentCards.vue';
import ContentSerietv from './ContentSerietv.vue';



export default {
    name: "FilmCards",
    props: {
        films: Array,
        serietvs: Array
    },
    components: { 
        ContentCards,
        ContentSerietv
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