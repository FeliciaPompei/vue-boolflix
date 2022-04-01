<template>
    <main class="container p-3 mt-4">
        <div class="row justify-content-center">
            <div class="col-12">
                <!-- testing loop -->
                <h1 class="text-info"> You search for {{getQuery}} </h1>
                <FilmCard
                v-for="(film, index) in getFilmList"
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
    props:{'filmSearch' : String},
    components:{
        FilmCard,
    },
    data : function(){
        return{
            filmList : null,
            filmFilter : [],
            getQuery : '',
        }
    },
    methods : {
        queryInsert (){
            this.getQuery = this.filmSearch;
        },

        getFilmList(){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=b9ee4557c1925ad6441d410a26f3ca26&language=it-IT&query=mission')
            .then((result) => {
                console.table(result.data.results);
                this.filmList = result.data.results;
                console.log(this.filmList)
            })
            .catch((error) => {
                console.error(error);
            })
        }
    },
    computed : {
    //     filmFiliter(){
    //         if(this.filmSearch == ''){
    //         return this.filmList
    //     }
    //         return this.filmList.filter((element) => element.title.toLowerCase().includes(this.filmSearch.toLowerCase()));
    //     }
    }
}
</script>

<style lang="scss" scoped>

</style>