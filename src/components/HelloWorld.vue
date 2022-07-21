<template>
  <div class="container">
    <div class="input-group m-3">
      <input type="text" class="form-control" placeholder="Search..." aria-label="Search" aria-describedby="basic-addon1" v-model.trim="getSearchItem">
    </div>
    <button class="btn btn-primary text-center m-3" @click="$emit('search', getSearchItem.toLowerCase())">Search</button>
    <ul>
      <li v-for="(film, index) in filmList" :key="index">{{film.title}}</li>
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