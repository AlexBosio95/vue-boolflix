<template>
    <main>
      <div class="container">
          <div class="cards-container d-flex flex-wrap my-4">

            <Cards v-for="film in movieList" :key="film.id"

                :title = 'film.title'
                :originalTitle = 'film.original_title'
                :originalLanguage = 'film.original_language'
                :vote = 'film.vote_average'
                :img = 'film.poster_path'
            />

            <Cards v-for="serie in seriesList" :key="serie.id"

                :title = 'serie.name'
                :originalTitle = 'serie.original_name'
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
  height: 90vh;
  background-color: $bgMainColor;
  overflow-y: auto;
}

</style>