<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">{{seriesItem.name}} </h5>
        <p class="card-text"> {{seriesItem.original_name}} </p>
        <p class="card-text"> {{seriesItem.original_language}} </p>
        <img :alt="this.flag" :src="`http://purecatamphetamine.github.io/country-flag-icons/3x2/${this.flag}.svg`"/>
        <p class="card-text"> {{seriesItem.vote_average}} </p>
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
    }
}

</script>

<style lang="scss" scoped>
.card{
    background-color:palevioletred;
    width:200px;
}
</style>