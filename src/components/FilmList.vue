<template>
    <main class="container p-3 mt-4">
        <div class="row justify-content-center">
            <div class="col-12">
                <FilmCard
                v-for="(film, index) in filmFiliter"
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
    props:['filmSearch'],
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
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=b9ee4557c1925ad6441d410a26f3ca26')
            .then((result) => {
                this.filmList = result.results;
                console.log(this.filmList)
            })
            .catch((error) => {
                console.error(error);
            })
        }
    },
    computed : {
        filmFiliter(){
            return this.filmList.filter((element) => element.title.toLowerCase().includes(this.filmSeach.toLowerCase()));
        }
    }
}
</script>

<style lang="scss" scoped>

</style>