<template>
  <div id="app">
    <Header
    @filmSearchInput = 'userRequest'
    />
    <SearchList
    :filmList = 'filmList'
    :tvSerieList = 'tvSerieList'
    />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import SearchList from './components/SearchList.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    SearchList
  },
  data : function(){
    return{
      userSearch : '',
      filmList : null,
      tvSerieList : null,
    }
  },
  methods : {
    userRequest(query){
      this.userSearch = query;
      console.log(this.userSearch);
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=b9ee4557c1925ad6441d410a26f3ca26&language=it-IT&query=${this.userSearch}`)
      .then((result) => {
          this.filmList = result.data.results;
          console.log(this.filmList)
      })
      .catch((error) => {
          console.error(error);
      });
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=b9ee4557c1925ad6441d410a26f3ca26&language=it_IT&query=${this.userSearch}`)
      .then((res) => {
          this.tvSerieList = res.data.results;
          console.log(this.tvSerieList)
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


//<img
      :src="`http://image.tmdb.org/t/p/w185${itemData.poster_path}`"
      :alt="itemData.title"
    />