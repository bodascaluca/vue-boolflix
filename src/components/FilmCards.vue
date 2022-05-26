<template>

    <div>
        <h2>Film</h2>
        <div class="row" v-if="films.length">
            <div class="card" v-for="(item, index) in films" :key="index">
                <ContentCards :item="item"/>
            </div>
        </div>
        <h1 v-else>Non ci sono film</h1>            

        <h2>Serie tv</h2>
    <div class="row">
        <div class="card" v-for="(serietv) in serietvs" :key="serietv.id">
            <ContentSerietv :serietv="serietv"/>
        </div>
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
    .row{
        display:flex;
        border:1px solid blue;
        height: 400px;
        overflow: hidden;
        overflow-x:auto;
    }

    .card{
        display: flex;
        align-items: center;
        margin:5px;
        border:1px solid red;
    }
</style>