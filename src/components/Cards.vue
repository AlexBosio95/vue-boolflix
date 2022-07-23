<template>
    <div class="ms_card position-relative">

        <div class="description position-absolute p-3">
            <!-- Titolo -->
            <h5>{{title}}{{name}}</h5>

            <!-- Titolo originale -->
            <p class="">{{originalTitle}}{{originalName}}</p>

            <!-- Flag -->
            <div class="flag-container my-3">
                <div :class="(originalLanguage == 'it') ? 'itFlag' : (originalLanguage == 'en') ? 'enFlag' : 'noFlag'"></div>
            </div>

            <!-- Star -->

            <div class="d-flex position-relative star-container">
                <!-- <span v-for="(star,index) in getStar()" :key="index">&#11088;</span> -->

                <div class="position-absolute">
                    <i v-for="(star,index) in getStar()" :key="index" class="fa-solid fa-star"></i>
                </div>

                <div class="position-absolute">
                    <i class="fa-regular fa-star"></i>
                    <i class="fa-regular fa-star"></i>
                    <i class="fa-regular fa-star"></i>
                    <i class="fa-regular fa-star"></i>
                    <i class="fa-regular fa-star"></i>
                </div>
          </div>

        </div>

        <!-- Img Cover -->
        <img :src="(img == null || img == '') ? 'https://demofree.sirv.com/nope-not-here.jpg' : `https://image.tmdb.org/t/p/w342/${img}`" :alt="(img)">

    </div>
  

</template>

<script>
export default {
    props:  {
    title: String,
    name: String,
    originalTitle: String,
    originalName: String,
    originalLanguage: String,
    vote: Number,
    img: String,
  },

  data() {
      return {
        numero: Math.round(this.vote / 2),
      }
    },

    methods: {

      getStar: function () {
        let arrayStar = []

        for (let i = 0; i < this.numero; i++) {
          arrayStar.length++
        }
        console.log(arrayStar)

        return arrayStar
      }
    }

}
</script>

<style lang="scss" scoped>

@import '../style/variabiles.scss';

.ms_card{
    width: calc(100% / 5 - 4px);
    min-height: 378px;
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
        height: 3rem;
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