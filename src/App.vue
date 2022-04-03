<template>
  <div id="app">
    <Header
    @filmSearchInput = 'filmRequest'
    />
    <FilmList
    :filmList = 'filmList'
    />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import FilmList from './components/FilmList.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    FilmList
  },
  data : function(){
    return{
      filmSearch : '',
      filmList : null,
    }
  },
  methods : {
    filmRequest(query){
      this.filmSearch = query;
      console.log(this.filmSearch);
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=b9ee4557c1925ad6441d410a26f3ca26&language=it-IT&query=${this.filmSearch}`)
      .then((result) => {
          this.filmList = result.data.results;
      })
      .catch((error) => {
          console.error(error);
      })
    }
  }
}
</script>

<style lang="scss">
@import'./assets/styles/style.scss';
body{
  background-color: rgb(12, 12, 81);
}
</style>
