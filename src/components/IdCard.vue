<template>
    <div class="card m-3">
        <div class="card-image" v-if="idCard.poster_path !== null">
            <img class="card-img-top img-fluid"  :src="`http://image.tmdb.org/t/p/w185${idCard.poster_path}`" :alt="idCard.original_title">
        </div>
        <div v-else>
            <img class="card-img-top img-fluid" src="https://adriaticaindustriale.it/wp-content/uploads/2020/02/not-found.png"  :alt="idCard.name || idCard.title">
        </div>
        <div class="card-body text-white">
            <h1 class="card-title my-font-color">{{idCard.original_title}}  {{idCard.original_name}} </h1>
            <p class="card-text" v-show="idCard.original_title !== idCard.original_title"> {{idCard.original_title}}  {{idCard.original_name}}</p>
            <p class="card-text">vote :{{voteAverage}} </p>
            <p>Lauguage: <flag :iso="flagTransform" /></p>
            <p v-if="idCard.overview != ''">Overview: {{idCard.overview}} </p>
            <p v-else>Overview: Watch the film/tv-show to find out what it's about </p>
            
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
    width:calc(100% / 4 - 4rem);
    position:relative;
    .card-img-top{
        width:100%;
        height:100%;
        object-fit: cover;
        
    }
    .card-body {
        display:none;
        background-color:rgba(0, 0, 0, 0.8);
        position:absolute;
        top:0;
        left:0;
        width:100%;
        height:100%;
        font-size: 1.2rem;
        overflow:auto;
        .my-font-color{
            color: #01E165;
        }
    }
}
.card:hover .card-body{
    display:block;
}
</style>