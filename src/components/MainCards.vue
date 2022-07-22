<template>
    <div class="container">
        <div class="cards-container d-flex flex-wrap">
                <Cards v-for="movie in movieList" :key="movie.id" 

                    :title = 'movie.title'
                    :name = 'movie.name'
                    :originalTitle = 'movie.original_title'
                    :originalName = 'movie.original_name'
                    :originalLanguage = 'movie.original_language'
                    :vote = 'movie.vote_average'
                    :img = 'movie.poster_path'
                />
        </div>
    

    </div>
</template>

<script>

import Cards from './Cards.vue'

export default {

  components: { 
      Cards 
    },

    props:{
    movieList: Array,
  },

}
</script>

<style lang="scss" scoped>



</style>