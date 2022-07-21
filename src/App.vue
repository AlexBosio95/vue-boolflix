<template>
  <div id="app">
    <HelloWorld 
    :filmList= 'filmList'
    @search = 'getApiRequest'/>
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
      filmList: [],
    }
  },
  methods: {
    getApiRequest(searchText){
      axios.get('https://api.themoviedb.org/3/search/movie', { params: { query:searchText, api_key : '5ff24ba7734ff867e412b5136fda3d11' } })
      .then((results) => {
        this.filmList = results.data.results;
      })   
    }
  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss'
</style>
