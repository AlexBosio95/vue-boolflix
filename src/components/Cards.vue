<template>
    <div class="card">

        <div class="description">
                <!-- Titolo -->
            <h5>{{title}}{{name}}</h5>

            <!-- Titolo originale -->
            <p class="">{{originalTitle}}{{originalName}}</p>

            <!-- Flag -->
            <div class="flag-container my-3">
                <div :class="(originalLanguage == 'it') ? 'itFlag' : (originalLanguage == 'en') ? 'enFlag' : 'noFlag'"></div>
            </div>

            <!-- Vote -->
            <!-- <p class="m-0">Vote: {{vote}}</p> -->

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

.card{
    width: calc(100% / 5 - 10px);
    margin: 5px;
    padding: 10px;

    img{
        width: 100%;
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