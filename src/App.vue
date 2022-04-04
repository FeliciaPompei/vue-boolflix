<template>
  <div id="app">
    <Header
    @filmSearchInput = 'userRequest'
    />
    <main class="container">
      <div class="row justify-content-center" :class="(filmList == '') ? 'd-none' : 'd-block'">
        <h1 class="text-white">Movies</h1>
        <div class="col-12 d-flex flex-wrap">
            <IdCard v-for="(film, index) in filmList" 
            :key="index" 
            :idCard ="film"
            />
        </div>
      </div>
      <div class="row justify-content-center" :class="(filmList == '') ? 'd-block' : 'd-none'">
          <h1 class="text-white">There is no movies with that name</h1>
      </div>
      <div class="row justify-content-center" :class="(tvSerieList == '') ? 'd-none' : 'd-block'">
        <h1 class="text-white">TV Series</h1>
        <div class="col-12 d-flex flex-wrap">
          <IdCard   v-for="(series, index) in tvSerieList" 
          :key="index" 
          :idCard ="series" 
          />
        </div>
      </div>
      <div class="row justify-content-center" :class="(tvSerieList == '') ? 'd-block' : 'd-none'">
        <h1 class="text-white">There is no series with that name</h1>
      </div>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import IdCard from './components/IdCard.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    IdCard
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
  background-color:#031732;
}
</style>