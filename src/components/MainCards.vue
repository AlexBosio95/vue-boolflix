<template>
    <main>
      <div class="container">

        <h3 class="title">{{title}}</h3>
        
        <h5 class="title">films</h5>
        <span>Total Films: {{totalFilms}}</span>

          <div class="cards-container d-flex mt-2">
            <h3 class="no_item" v-if="(totalFilms <= 0)">No content available</h3>

            <Cards v-for="film in movieList" :key="film.id"

                :title = 'film.title'
                :originalTitle = 'film.original_title'
                :originalLanguage = 'film.original_language'
                :vote = 'film.vote_average'
                :img = 'film.poster_path'
                :nVote = 'film.vote_count'
                :dateRelease = 'film.release_date'
            />

          </div>

          <span v-if="(totalFilms > 5)" class="w-100 d-inline-block text-end mt-1 opacity-25">Scroll for more movies <i class="fa-solid fa-angles-right"></i></span>


          <h5 class="title">TV series</h5>
          <span>Total Series: {{totalSeries}}</span>

          <div class="cards-container d-flex my-2">
            <h3 class="no_item" v-if="(totalSeries <= 0)">No content available</h3>

            <Cards v-for="serie in seriesList" :key="serie.id"

                :title = 'serie.name'
                :originalTitle = 'serie.original_name'
                :originalLanguage = 'serie.original_language'
                :vote = 'serie.vote_average'
                :img = 'serie.poster_path'
                :nVote = 'serie.vote_count'
                :dateRelease = 'serie.release_date'
            />
          
          </div>

          <span v-if="(totalSeries > 5)" class="w-100 d-inline-block text-end mt-1 opacity-25">Scroll for more movies <i class="fa-solid fa-angles-right"></i></span>

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
    totalFilms: Number,
    totalSeries: Number,

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

  .no_item{
    text-align: center;
    display: inline-block;
    width: 100%;
    color: white;
    opacity: 0.5;
  }

  .cards-container{
    overflow-x: auto;
    min-height: 385px;
  }
}

</style>