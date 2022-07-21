<template>
  <div id="app">
    <HelloWorld 
    :filmList= 'filmList'
    @search = 'getApiRequest'/>
    <div class="container text-center">
      <h2 v-if="isEmpty" class="">List is Empty...</h2>
    </div>
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
      isEmpty: true,
    }
  },
  methods: {
    getApiRequest(searchText){
      this.isEmpty = true
      console.log(searchText)
      this.filmList = []
      if(!searchText == null || !searchText == '') {   
        axios.get('https://api.themoviedb.org/3/search/movie', { params: { query:searchText, api_key : '5ff24ba7734ff867e412b5136fda3d11' } })
        .then((results) => {
          this.filmList = results.data.results;
          this.isEmpty = false
        }).catch((error) => {
          console.warn(error)
        })   
      } else{
        console.warn(searchText)
        this.isEmpty = true
      }
      console.log(this.isEmpty)
    },
  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss'
</style>
