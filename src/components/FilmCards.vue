<template>

    <div>
        <h1>Film</h1>
        <div class="row" v-if="films.length">
            <div class="card" v-for="(item, index) in films" :key="index">
                <ContentCards :item="item"/>
            </div>
        </div>
        <h2 class="heightMin" v-else>Se vuoi puoi cercare altri Film...</h2>            

        <h1>Serie tv</h1>
        <div class="row" v-if="serietvs.length">
            <div class="card" v-for="(serietv) in serietvs" :key="serietv.id">
                <ContentSerietv :serietv="serietv"/>
            </div>
         </div>
        <h2 class="heightMin" v-else>Se vuoi puoi cercare altre SerieTv...</h2>            
         
   
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

    .heightMin{
         height:400px;
         margin-top:1rem;
    }

    h1{
        color: white;
    }

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