<template>
  <div id="app">
    <Header
    @filmSearchInput = 'filmRequest'
    />
    <FilmList
    :filmSearch = 'filmSearch'
    />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import FilmList from './components/FilmList.vue'

export default {
  name: 'App',
  components: {
    Header,
    FilmList
  },
  data : function(){
    return{
      filmSearch : '',
    }
  },
  methods : {
    filmRequest(filmSearchInput){
      this.filmSearch = filmSearchInput;
    }
  }
}
</script>

<style lang="scss">
@import'./assets/styles/style.scss';
body{
  background-color: rgb(12, 12, 81);
  color:white;
}
</style>
