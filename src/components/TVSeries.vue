<template>
    <div class="card">
        <img :src="`http://image.tmdb.org/t/p/w185${seriesItem.poster_path}`" class="card-img-top" :alt="seriesItem.name">
        <div class="card-body">
            <h5 class="card-title">{{seriesItem.name}} </h5>
        <p class="card-text"> {{seriesItem.original_name}} </p>
        <p class="card-text"> {{seriesItem.original_language}} </p>
        <img :alt="this.flag" :src="`http://purecatamphetamine.github.io/country-flag-icons/3x2/${this.flag}.svg`"/>
        <p class="card-text"> {{selectVote}} </p>
        </div>
    </div>
</template>

<script>
export default {
    name:'TVSeries',
    props : ['seriesItem'],
    data(){
        return{
            flag : '',
        }
    },
    methods :{
        hasFlag(){
            if(this.seriesItem.original_language === 'en'){
                return this.flag = 'GB'
            } else if(this.seriesItem.original_language === 'it'){
                return this.flag = 'IT'
            } else{
                return this.flag = 'US'
            }
        }
    },
    mounted(){
        this.hasFlag
    },
    computed : {
        selectVote() {
            const vote = this.seriesItem.vote_average;
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
    background-color:palevioletred;
    width:200px;
}
</style>