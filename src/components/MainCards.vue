<template>
    <div class="container">

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

.flag-container{
  height: 1rem;
  width: 1.8rem;

    .itFlag{
    background-image: url('https://upload.wikimedia.org/wikipedia/commons/0/03/Flag_of_Italy.svg');
    background-size: cover;
    height: 1rem;
    }

    .enFlag{
    background-image: url('https://upload.wikimedia.org/wikipedia/en/thumb/a/ae/Flag_of_the_United_Kingdom.svg/1200px-Flag_of_the_United_Kingdom.svg.png');
    background-size: cover;
    height: 1rem;
    }

    .noFlag{
      background-image: url('https://upload.wikimedia.org/wikipedia/commons/thumb/b/b0/No_flag.svg/2560px-No_flag.svg.png');
      background-size: cover;
      height: 1rem;
    }

}

</style>