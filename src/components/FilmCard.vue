<template>
    <div class="card">
        <img :src="`http://image.tmdb.org/t/p/w185${filmItem.poster_path}`" class="card-img-top" :alt="filmItem.original_title">
        <div class="card-body">
            <h5 class="card-title">{{filmItem.original_title}} </h5>
        <p class="card-text"> {{filmItem.original_title}} </p>
        <p class="card-text"> {{filmItem.original_language}} </p>
        <p class="card-text"> {{voteAverage}} </p>
        </div>
    </div>
</template>

<script>
export default {
    name:'FilmCard',
    props : ['filmItem'],
    computed : {
        voteAverage() {
            const vote = this.filmItem.vote_average;
            if (vote < 2) return "★";
            if (vote > 2 && vote < 4) return "★★";
            if (vote > 4 && vote < 6) return "★★★";
            if (vote > 6 && vote < 8) return "★★★★";
            if (vote > 8 && vote <= 10) return "★★★★★";
            return "";
        },
    }
}
</script>

<style lang="scss" scoped>
.card{
    background-color:palegreen;
    width:200px;
}
</style>