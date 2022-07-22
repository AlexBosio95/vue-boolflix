<template>
  <div id="app">

    <HeaderSite 
    @search = 'getApiRequest'/>

    <MainCards 
    :movieList= 'movieList'/>

    <div class="container text-center">
      <h2 v-if="isEmpty" class="">List is Empty...</h2>
    </div>

  </div>
</template>

<script>
import HeaderSite from './components/HeaderSite.vue';
import MainCards from './components/MainCards.vue';

import axios from 'axios';

export default {
  name: 'App',
  components: {
    HeaderSite,
    MainCards,
  },
  data: function(){
    return{
      movieList: [],
      isEmpty: true,
    }
  },
  methods: {
    getApiRequest(searchText){
      this.isEmpty = true
      console.log(searchText)
      this.movieList = []
      if(!searchText == null || !searchText == '') {   
        axios.get('https://api.themoviedb.org/3/search/movie', { params: { query:searchText, api_key : '5ff24ba7734ff867e412b5136fda3d11' } })
        .then((results) => {
          this.movieList = results.data.results;
          if (this.movieList.length <= 0) {
            this.isEmpty = true
          } else {
            this.isEmpty = false
          }
        }).catch((error) => {
          console.warn(error)
        })
 
        axios.get('https://api.themoviedb.org/3/search/tv', { params: { query:searchText, api_key : '5ff24ba7734ff867e412b5136fda3d11' } })
        .then((results) => {
          this.movieList = results.data.results;
          if (this.movieList.length <= 0) {
            this.isEmpty = true
          } else {
            this.isEmpty = false
          }
        }).catch((error) => {
          console.warn(error)
        })

      } else{
        this.isEmpty = true
      }
    },
  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss'
</style>
