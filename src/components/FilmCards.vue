<template>
    <div >
        <div class="card">
         <h1>Titolo</h1>
        <h2>Titolo Originale</h2>
        <h3>Lingue</h3>
        <h4>Voto</h4>
        </div>
    
    </div>
</template>

<script>
export default {
    name:"FilmCards",
}
</script>

<style scoped lang="scss">
@import "../style/common.scss";
    .card{
        margin:1rem;
        border:1px solid red;
        width: 200px;
    }
</style>