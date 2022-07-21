<template>
  <div class="container">
    <div class="input-group m-3">
      <input type="text" class="form-control" placeholder="Search..." aria-label="Search" aria-describedby="basic-addon1" v-model.trim="getSearchItem">
    </div>
    <button class="btn btn-primary text-center m-3" @click="$emit('search', getSearchItem.toLowerCase())">Search</button>
    <ul class="list-group p-4">
      <li class="list-group-item" v-for="(film, index) in filmList" :key="index">
        <h5>{{film.title}}</h5>
        <p>{{film.original_title}}</p>
        <p>Language = {{film.original_language}}</p>
        <p>Vote: {{film.vote_average}}</p>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
  props:{
    filmList: Array,
  },
  data: function(){
    return{
      getSearchItem: '',
    }
  },
  methods: {

  }

}
</script>

<style>

</style>