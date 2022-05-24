<template>
    <div class="flex" >
    
    <h2>Film</h2>

    <div class="card" v-for="(item, index) in films" :key="index">
        <ContentCards  :item="item"/>
    </div>

    <h2>Serie tv</h2>

    <div class="card" v-for="(serietv) in serietvs" :key="serietv.id">
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