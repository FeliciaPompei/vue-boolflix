<template>
    <main class="container p-3 mt-4">
        <div class="row justify-content-center" :class="(filmList == '') ? 'd-none' : 'd-block'">
            <h1 class="text-white">Movies</h1>
            <div class="col-12 d-flex flex-wrap">
                <FilmCard v-for="(film, index) in filmList" 
                :key="index" 
                :filmItem ="film"
                
                />
            </div>
        </div>
        <div class="row justify-content-center" :class="(tvSerieList == '') ? 'd-none' : 'd-block'">
            <h1 class="text-white">TV Series</h1>
            <div class="col-12 d-flex flex-wrap">
                <TVSeries  v-for="(series, index) in tvSerieList" 
                :key="index" 
                :seriesItem ="series" 
                />
            </div>
        </div>
    </main>
</template>

<script>
import FilmCard from './FilmCard.vue';
import TVSeries from './TVSeries.vue';

export default {
    name:'IndexSearchList',
    props:{'filmList' : Array,
    'tvSerieList' : Array},
    
    components:{
        FilmCard,
        TVSeries,
    },
}
</script>

<style lang="scss" scoped>

</style>