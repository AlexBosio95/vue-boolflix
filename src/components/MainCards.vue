<template>
    <main>
      <div class="container">
        <h5 class="title">{{title}}</h5>
        <span>Total movies: {{totalMovie}}</span>
          <div class="cards-container d-flex my-4">

            <Cards v-for="film in movieList" :key="film.id"

                :title = 'film.title'
                :originalTitle = 'film.original_title'
                :originalLanguage = 'film.original_language'
                :vote = 'film.vote_average'
                :img = 'film.poster_path'
                :nVote = 'film.vote_count'
            />

            <Cards v-for="serie in seriesList" :key="serie.id"

                :title = 'serie.name'
                :originalTitle = 'serie.original_name'
                :originalLanguage = 'serie.original_language'
                :vote = 'serie.vote_average'
                :img = 'serie.poster_path'
                :nVote = 'serie.vote_count'
            />
          </div>
        </div>
    

    </main>
</template>

<script>

import Cards from './Cards.vue'

export default {

  components: { 
      Cards 
    },

    props:{
    movieList: Array,
    seriesList: Array,
    title: String,
    totalMovie: Number,
  },
  data: function(){
    return{
      
    }
  }

}
</script>

<style lang="scss" scoped>
@import '../style/variabiles.scss';

main{
  height: 90vh;
  background-color: $bgMainColor;
  overflow-y: auto;

  .title{
    text-transform: uppercase;
    color: white;
    margin-top: 20px;
    margin-bottom: 0;
  }

  span{
    color: white;
    opacity: 0.7;
    font-size: 0.8rem;
  }

  .cards-container{
    overflow-x: auto;
  }
}

</style>