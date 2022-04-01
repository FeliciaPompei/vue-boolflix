<template>
    <main class="container p-3 mt-4">
        <div class="row justify-content-center">
            <div class="col-12">
                <FilmCard
                v-for="(film, index) in filmList"
                :key="index"
                :film = "film"
                />
            </div>
        </div>
    </main>
</template>

<script>
import FilmCard from './FilmCard.vue';
import axios from 'axios';
export default {
    name:'IndexFilmList',
    components:{
        FilmCard,
    },
    data : function(){
        return{
            filmList : [],
        }
    },
    methods : {
        getFilmList(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((result) => {
                this.filmList = result.data.results;
                console.log(this.filmList)
            })
            .catch((error) => {
                console.error(error);
            })
        }
    }
}
</script>

<style lang="scss" scoped>

</style>