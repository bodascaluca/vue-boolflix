<template>
  <div>
       <h1> SERIE TV{{ serietv.name}}</h1>
            <h2>{{ serietv.original_name}}</h2>
            <img class="img-flag" v-if="hasimage(serietv)" :src="require(`../assets/img/` + serietv.original_language + `.jpg`)" alt=""/>
            <p v-else> {{ serietv.original_language}}</p>
            <h4>{{ serietv.vote_average}}</h4>
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
        }
    },
}
</script>

<style scoped lang="scss">
@import "../style/common.scss";

.img-flag{
        width: 20px;
    }

</style>