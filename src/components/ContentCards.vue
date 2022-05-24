<template>
  <div>
            <h1>{{ item.title}}</h1>
            <h2>{{ item.original_title}}</h2>
            <img class="img-flag" v-if="hasimage(item)" :src="require(`../assets/img/` + item.original_language + `.jpg`)" alt=""/>
            <p v-else> {{ item.original_language}}</p>
            <h4>{{ item.vote_average}}</h4>
  </div>
</template>

<script>
export default {
    name:"ContentCards",
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
        }
    },
}
</script>

<style scoped lang="scss">

     .img-flag{
        width: 20px;
    }
</style>