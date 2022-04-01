<template>
    <main class="container p-3 mt-4">
        <div class="row justify-content-center">
            <div class="col-12 d-flex flex-wrap">
                <FilmCard v-for="(film, index) in filmList" 
                :key="index" 
                :filmItem ="film" />
            </div>
        </div>
    </main>
</template>

<script>
import FilmCard from './FilmCard.vue';
export default {
    name:'IndexFilmList',
    props:{'filmList' : Array},
    
    components:{
        FilmCard,
    },
}
</script>

<style lang="scss" scoped>

</style>