<template>
  <div id="app">

    <HeaderSite 
    @search = 'getApiRequest'/>

    <MainCards 
    :movieList= 'movieList'
    :seriesList = 'seriesList'
    :title="title"/>

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
      seriesList: [],
      isEmpty: true,
      apiKey: '5ff24ba7734ff867e412b5136fda3d11',
      title: ''
    }
  },
  methods: {
    getApiRequest(searchText){
      this.isEmpty = true
      console.log(searchText)
      this.movieList = []
      this.seriesList = []

      if(!searchText == null || !searchText == '') {   
        axios.get('https://api.themoviedb.org/3/search/movie', { params: { query:searchText, api_key : this.apiKey } })
        .then((results) => {
          this.movieList = results.data.results;
          this.title = 'result'
          
        }).catch((error) => {
          console.warn(error)
        })
 
        axios.get('https://api.themoviedb.org/3/search/tv', { params: { query:searchText, api_key : this.apiKey } })
        .then((results) => {
          this.seriesList = results.data.results;
          this.title = 'result'

        }).catch((error) => {
          console.warn(error)
        })

      } else{
        console.log('error')
        this.title = 'no items'
      }
    },
    getApiRequestTrendign(){
       axios.get('https://api.themoviedb.org/3/trending/all/day?', { params: { api_key : this.apiKey } })
        .then((results) => {
          this.movieList = results.data.results;
          console.log(results.data.results)
          this.title = 'Trending'
        }).catch((error) => {
          console.warn(error)
        })

    }
  },
  created(){
    this.getApiRequestTrendign()
  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss'
</style>
