<template>
  <div class="container">
    <div class="input-group m-3">
      <input type="text" class="form-control" placeholder="Search..." aria-label="Search" aria-describedby="basic-addon1" v-model.trim="getSearchItem" @keypress.enter="$emit('search', getSearchItem.toLowerCase())">
    </div>
    <button class="btn btn-primary m-3" @click="$emit('search', getSearchItem.toLowerCase())">Search</button>
    <ul class="list-group p-4">
      <li class="list-group-item" v-for="(movie, index) in movieList" :key="index">
        <h5>{{movie.title}}{{movie.name}}</h5>
        <p class="m-0">{{movie.original_title}}{{movie.original_name}}</p>
        <!-- <span class="m-0">Language = {{movie.original_language}}</span> -->
        <div class="flag-container">
          <div :class="(movie.original_language == 'it') ? 'itFlag' : (movie.original_language == 'en') ? 'enFlag' : 'noFlag'"></div>
        </div>
        <div class="d-flex">
          
        </div>
        <p class="m-0">Vote: {{movie.vote_average}}</p>
        <img :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" :alt="(movie.poster_path)">
        </li>
    </ul>
  </div>
</template>

<script>
export default {
  props:{
    movieList: Array,
  },
  data: function(){
    return{
      getSearchItem: '',
      numero: Math.round(this.movieList.vote_average / 2),
    }
  },
  methods: {
    

  }

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