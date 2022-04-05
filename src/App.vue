<template>
  <div id="app">
    <Header
    @filmSearchInput = 'userRequest'
    />
    <main>
      <div class="container-fluid" v-if="filmList">
        <div class="row justify-content-center mb-5" :class="(filmList == '') ? 'd-none' : 'd-block'">
          <div class="film-type-list mb-4">
            <h1 class="m-0">Movies</h1>
          </div>
          <div class="col-12 d-flex flex-wrap justify-content-center">
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
          <div class="film-type-list mb-4 justify-content-center">
            <h1 class="m-0">TV Series</h1>
          </div>
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
      </div>
      <div v-else>
        <div class="container-fluid">
          <div class="row">
            <div class="col-12 p-0">
              <Slider
              :sliderImg = "sliderFilmList"
              />
            </div>
          </div>
        </div>
        <div class="container-fluid">
          <div class="row justify-content-center">
            <div class="film-type-list mb-4 me-auto">
            <h1 class="m-0">Top Rated</h1>
          </div>
            <div class="col-12 d-flex flex-wrap justify-content-center">
                <IdCard v-for="(film, index) in reacentFilmList" 
                :key="index" 
                :idCard ="film"
                />
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import IdCard from './components/IdCard.vue';
import Slider from './components/Slider.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    IdCard,
    Slider
  },
  data : function(){
    return{
      userSearch : '',
      filmList : null,
      tvSerieList : null,
      reacentFilmList : null,
      sliderFilmList : null,
    }
  },
  methods : {
    getReacentFilmList(){
      axios.get(`https://api.themoviedb.org/3/movie/top_rated?api_key=b9ee4557c1925ad6441d410a26f3ca26&language=it-IT&page=1`)
      .then((result) => {
          this.reacentFilmList = result.data.results;
          console.log(this.reacentFilmList)
      })
      .catch((error) => {
          console.error(error);
      });
    },
    getPopularFilm(){
      axios.get(`https://api.themoviedb.org/3/movie/popular?api_key=b9ee4557c1925ad6441d410a26f3ca26&language=en-US&page=1`)
      .then((result) => {
          this.sliderFilmList = result.data.results;
          console.log(this.sliderFilmList)
      })
      .catch((error) => {
          console.error(error);
      });
    },
    userRequest(query){
      if(query != ''){
        this.userSearch = query;
      console.log(this.userSearch);
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=b9ee4557c1925ad6441d410a26f3ca26&query=${this.userSearch}`)
      .then((result) => {
          this.filmList = result.data.results;
          console.log(this.filmList)
      })
      .catch((error) => {
          console.error(error);
      });
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=b9ee4557c1925ad6441d410a26f3ca26&query=${this.userSearch}`)
      .then((res) => {
          this.tvSerieList = res.data.results;
          console.log(this.tvSerieList)
      })
      .catch((error) => {
          console.error(error);
      })
      } else{
        this.filmList = '';
        this.tvSerieList = '';
      }
    }
  },
  created(){
    this.getReacentFilmList()
    this.getPopularFilm()
  }
}
</script>

<style lang="scss">
@import'./assets/styles/style.scss';
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');
body{
  background-color:#031732;
  font-family: 'Bebas Neue', cursive;

  .film-type-list{
    background-color:#01E165;
    width:50%;
    padding:0.5rem 1rem;
    
    h1{
      font-size: 3rem;
    }
  }
}
</style>