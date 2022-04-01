<template>
  <div id="app">
    <Header/>
    <FilmList/>
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
