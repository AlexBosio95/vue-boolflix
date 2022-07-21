<template>
  <div id="app">
    <HelloWorld 
    :filmList= 'filmList'
    @search = 'searchFilm'/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data: function(){
    return{
      apiSrcUrl: 'https://api.themoviedb.org/3/search/movie?api_key=5ff24ba7734ff867e412b5136fda3d11&query=',
      filmList: [],
      searchPath: '',
    }
  },
  methods: {
    getApiRequest(){
      axios.get(this.searchPath)
      .then((results) => {
        this.filmList = results.data.results;
      })
    },
    searchFilm(searchText){
      this.searchPath = this.apiSrcUrl + searchText
      console.log(this.searchPath)
    }
  },
  created(){
    this.getApiRequest();
  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss'
</style>
