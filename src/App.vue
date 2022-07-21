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
      apiSrcUrl: 'https://api.themoviedb.org/3/search/movie?api_key=5ff24ba7734ff867e412b5136fda3d11&query=',
      filmList: [],
    }
  },
  methods: {
    getApiRequest(searchText){
      let searchPath
      searchPath = this.apiSrcUrl + searchText
      console.log(searchPath)

      axios.get(searchPath)
      .then((results) => {
        this.filmList = results.data.results;
      })
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
