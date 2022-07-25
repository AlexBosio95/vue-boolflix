<template>
    <div class="ms_card position-relative">

        <div class="description position-absolute p-3">
            <!-- Titolo -->
            <h5>{{title}}</h5>

            <!-- Titolo originale -->
            <p>{{originalTitle}}</p>

            <!-- Flag -->
            <div class="flag-container my-3">
                <div :class="(originalLanguage == 'it') ? 'itFlag' : (originalLanguage == 'en') ? 'enFlag' : 'noFlag'"></div>
            </div>

            <!-- Star -->
            <div class="d-flex position-relative star-container">

                  <div class="position-absolute">
                      <i v-for="(star,index) in getStar()" :key="index" class="fa-solid fa-star"></i>
                  </div>

                  <div class="position-absolute">
                      <i class="fa-regular fa-star" v-for="(n) in nrStar" :key="n"></i>
                  </div>
            </div>

            <!-- Vote Number -->
            <span>Total vote: {{nVote}}</span>

        </div>

        <!-- Img Cover -->
        <img :src="(img == null || img == '') ? 'https://demofree.sirv.com/nope-not-here.jpg' : `https://image.tmdb.org/t/p/w342/${img}`" :alt="(img)">

    </div>
  

</template>

<script>
export default {
    props:  {
    title: String,
    originalTitle: String,
    originalLanguage: String,
    vote: Number,
    img: String,
    nVote: Number,
  },

  data() {
      return {
        numero: Math.round(this.vote / 2),
        nrStar: 5,
      }
    },

    methods: {

      getStar: function () {
        let arrayStar = []

        for (let i = 0; i < this.numero; i++) {
          arrayStar.length++
        }
        return arrayStar
      },

      // getTitle(){
      //   if (this.title == '' || this.title == null) {
      //     this.title = 'No Title'
      //   } else {
      //     this.title
      //   }
      // },

      // getTitleOriginal(){
      //   if (this.originalTitle == '' || this.originalTitle == null) {
      //     this.originalTitle = 'No Title'
      //   } else {
      //     this.originalTitle
      //   }
      // },

    }

}
</script>

<style lang="scss" scoped>

@import '../style/variabiles.scss';

.ms_card{
    width: calc(100% / 5 - 4px);
    min-width: 255px;
    min-height: 385px;
    max-height: 385px;
    margin: 2px;
    background-color: $bgColor;
    cursor: pointer;

    &:hover img{
      opacity: 0.1;
    }

    img{
        width: 100%;
        height: 100%;
        object-fit: cover;
        overflow: hidden;
    }

    .description{
      color: white;
      width: 100%;
      display: none;
    }

    &:hover .description{
      display: block;
    }

    .star-container{
        height: 2rem;
    }

    .flag-container{
    height: 1rem;
    width: 1.8rem;

        .itFlag{
        background-image: url('https://upload.wikimedia.org/wikipedia/commons/0/03/Flag_of_Italy.svg');
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
        height: 1rem;
        }

        .enFlag{
        background-image: url('https://upload.wikimedia.org/wikipedia/en/thumb/a/ae/Flag_of_the_United_Kingdom.svg/1200px-Flag_of_the_United_Kingdom.svg.png');
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
        height: 1rem;
        }

        .noFlag{
        background-image: url('https://upload.wikimedia.org/wikipedia/commons/thumb/b/b0/No_flag.svg/2560px-No_flag.svg.png');
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
        height: 1rem;
        }

      }


}



</style>