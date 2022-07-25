<template>
  <div id="app">

    <HeaderSite 
    @search = 'getApiRequest'/>

    <MainCards 
    :movieList= 'movieList'
    :seriesList = 'seriesList'
    :title="title"
    :totalFilms= "totalFilms"
    :totalSeries= "totalSeries"/>

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
      apiSrc: 'https://api.themoviedb.org/3/search/',
      apiTrend: 'https://api.themoviedb.org/3/trending/all/day?',
      title: '',
      totalFilms: 0,
      totalSeries: 0,
    }
  },
  methods: {
    getApiRequest(searchText){
      this.isEmpty = true
      this.movieList = []
      this.seriesList = []
      this.totalFilms = 0
      this.totalSeries = 0

      if(!searchText == null || !searchText == '') {   
        axios.get(this.apiSrc + 'movie', { params: { query:searchText, api_key : this.apiKey } })
        .then((results) => {
          this.movieList = results.data.results;
          this.title = 'result';
          this.totalFilms = this.movieList.length;
          console.log(this.totalItems)

        }).catch((error) => {
          console.warn(error);
        })
 
        axios.get(this.apiSrc + 'tv', { params: { query:searchText, api_key : this.apiKey } })
        .then((results) => {
          this.seriesList = results.data.results;
          this.title = 'result';
          this.totalSeries = this.seriesList.length;
          console.log(this.totalItems)

        }).catch((error) => {
          console.warn(error);
        })

      } else{
        console.log('error')
        this.title = 'no items'
      }
    },
    getApiRequestTrendign(){
       axios.get(this.apiTrend, { params: { api_key : this.apiKey } })
        .then((results) => {
            this.movieList = results.data.results;
            this.totalFilms = this.movieList.length

            this.movieList.forEach(element => {
              if (element.media_type == 'tv') {
                this.seriesList.push(element)
              }
              this.totalSeries = this.seriesList.length
            });
          
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
