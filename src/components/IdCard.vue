<template>
    <div class="card">
        <div class="card-image" v-if="idCard.poster_path !== null">
            <img :src="`http://image.tmdb.org/t/p/w185${idCard.poster_path}`" class="card-img-top" :alt="idCard.original_title">
        </div>
        <div v-else>
            <img src="https://adriaticaindustriale.it/wp-content/uploads/2020/02/not-found.png" class="card-img-top" :alt="idCard.name || idCard.title">
        </div>
        
        <div class="card-body">
            <h5 class="card-title">{{idCard.original_title}} || {{idCard.original_name}} </h5>
        <p class="card-text"> {{idCard.original_title}} || {{idCard.original_name}}  </p>
        <flag :iso="flagTransform" />
        <p class="card-text"> {{voteAverage}} </p>
        </div>
    </div>
</template>

<script>
export default {
    name:'IdCard',
    props : ['idCard'],
    computed : {
        voteAverage() {
            const vote = this.idCard.vote_average;
            if (vote < 2) return "★";
            if (vote > 2 && vote < 4) return "★★";
            if (vote > 4 && vote < 6) return "★★★";
            if (vote > 6 && vote < 8) return "★★★★";
            if (vote > 8 && vote <= 10) return "★★★★★";
            return "";
        },
        flagTransform(){
            if(this.idCard.original_language === 'en'){
                return 'gb';
            } else if(this.idCard.original_language == 'us'){
                return 'us'
            }
            return this.idCard.original_language
        }
    }
}
</script>

<style lang="scss" scoped>
.card{
    background-color:palegreen;
    width:200px;
}
</style>