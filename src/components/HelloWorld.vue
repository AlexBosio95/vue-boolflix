<template>
  <div class="container">
    <div class="input-group m-3">
      <input type="text" class="form-control" placeholder="Search..." aria-label="Search" aria-describedby="basic-addon1" v-model.trim="getSearchItem" @keypress.enter="$emit('search', getSearchItem.toLowerCase()), getCurrentFlag()">
    </div>
    <button class="btn btn-primary m-3" @click="$emit('search', getSearchItem.toLowerCase()), getCurrentFlag()">Search</button>
    <ul class="list-group p-4">
      <li class="list-group-item" v-for="(film, index) in filmList" :key="index">
        <h5>{{film.title}}</h5>
        <p class="m-0">{{film.original_title}}</p>
        <span class="m-0">Language = {{film.original_language}}</span>
        <img :src="linkFlag" :alt="film.original_language">
        <p class="m-0">Vote: {{film.vote_average}}</p>
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
      linkFlag: '',
    }
  },
  methods: {
    getCurrentFlag: function(){
      this.filmList.forEach(element => {
        console.log(element.original_language)
        if(element.original_language == 'it'){
          this.linkFlag = 'https://upload.wikimedia.org/wikipedia/commons/0/03/Flag_of_Italy.svg'
        }
      });


    }
    

  }

}
</script>

<style lang="scss" scoped>

img{
  height: 1rem;
  margin-left: 0.5rem;
}

</style>