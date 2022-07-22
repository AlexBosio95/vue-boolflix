<template>
    <main>
      <div class="container">
          <div class="cards-container d-flex flex-wrap my-4">
            
            <Cards v-for="movie in movieList" :key="movie.id" 

                :title = 'movie.title'
                :originalTitle = 'movie.original_title'
                :originalLanguage = 'movie.original_language'
                :vote = 'movie.vote_average'
                :img = 'movie.poster_path'
            />

            <Cards v-for="serie in seriesList" :key="serie.id" 

                :name = 'serie.name'
                :originalName = 'serie.original_name'
                :originalLanguage = 'serie.original_language'
                :vote = 'serie.vote_average'
                :img = 'serie.poster_path'
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
    seriesList: Array
  },

}
</script>

<style lang="scss" scoped>
@import '../style/variabiles.scss';

main{
  height: 93vh;
  background-color: $bgMainColor;
  overflow-y: auto;
}

</style>