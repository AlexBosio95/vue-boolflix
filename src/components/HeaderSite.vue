<template>
  <header>
    <div class="container">
      <div class="row row-cols-2">
        <div class="col-8 d-flex align-items-center logo-container">
          <img src="../assets/Boolflix.png" alt="">
          <nav >
            <ul>
              <li v-for="(navitem, index) in navMenu" :key="index">{{navitem}}</li>
            </ul>
          </nav>
        </div>
        <div class="col-4 d-flex justify-content-end align-items-center search-container">

          <transition name="slide-fade" >
            <div class="input-group my-3" v-if="isOpen">
              <input type="text" class="form-control" placeholder="Search..." aria-label="Search" aria-describedby="basic-addon1" v-model.trim="getSearchItem" @keypress.enter="$emit('search', getSearchItem.toLowerCase())">
            </div>
          </transition>

          <div class="d-flex align-items-center">
            <i class="fa-solid fa-magnifying-glass" @click="isOpen = !isOpen"></i>
            <i class="fa-solid fa-bell"></i>
            <img src="https://upload.wikimedia.org/wikipedia/commons/0/0b/Netflix-avatar.png" alt="">
            <i class="fa-solid fa-sort-down"></i>
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
      navMenu: ['Home', 'Serie TV', 'Film', 'Originali', 'Aggiunti di recente', 'La mia Lista']
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

      ul{
        list-style: none;
        margin: 0;

        li{
          cursor: pointer;
          color: white;
          display: inline;
          padding: 0px 8px;
          opacity: 0.5;

          &:hover{
            opacity: 1;
          }
        }
      }

  }

  .search-container{
    height: 10vh;

      i{
        color: white;
        cursor: pointer;
      }

      .fa-magnifying-glass{
        padding-left: 10px;
      }

      .fa-bell{
        padding: 10px;
      }

      .fa-sort-down{
        padding-bottom: 6px;
      }

      img{
        height: 30px;
        margin-right: 10px;
      }

      input{
        background-color: $bgMainColor;
        color: white;
        border: none;
        max-width: 250px;
      }
  }
  
}

.slide-fade-enter-active {
  transition: all 0.3s ease-in-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}

</style>