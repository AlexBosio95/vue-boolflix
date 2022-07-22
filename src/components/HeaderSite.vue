<template>
  <header>
    <div class="container">
      <div class="row row-cols-2">
        <div class="col-8 d-flex align-items-center logo-container">
          <img src="../assets/Boolflix.png" alt="">
        </div>
        <div class="col-4 d-flex justify-content-end align-items-center search-container">
          <div>
            <i class="fa-solid fa-magnifying-glass" @click="openSearch()"></i>
          </div>
          <div class="input-group my-3" v-show="isOpen">
            <input type="text" class="form-control" placeholder="Search..." aria-label="Search" aria-describedby="basic-addon1" v-model.trim="getSearchItem" @keypress.enter="$emit('search', getSearchItem.toLowerCase())">
          </div>
        </div>
    </div>
    </div>
    
    
  </header>
</template>

<script>
export default {
  
  data: function(){
    return{
      getSearchItem: '',
      isOpen: false,
    }
  },
  methods: {
    openSearch(){
      this.isOpen = !this.isOpen
    }


  }

}
</script>

<style lang="scss" scoped>

@import '../style/variabiles.scss';

header{
  background-color: $bgColor;
  height: 10vh;

  .logo-container{
    height: 10vh;

      img{
        height: 3rem;
      }
  }

  .search-container{
    height: 10vh;

      i{
        color: white;
        padding: 15px;
        cursor: pointer;
      }

      input{
        background-color: $bgMainColor;
        color: white;
        border: none;
      }
  }



  
}

</style>