<template>
    <div class="card">

        <!-- Titolo -->
        <h5>{{title}}{{name}}</h5>

        <!-- Titolo originale -->
        <p class="m-0">{{originalTitle}}{{originalName}}</p>

        <!-- Flag -->
        <div class="flag-container">
            <div :class="(originalLanguage == 'it') ? 'itFlag' : (originalLanguage == 'en') ? 'enFlag' : 'noFlag'"></div>
        </div>

        <!-- Vote -->
        <p class="m-0">Vote: {{vote}}</p>

        <!-- Img Cover -->
        <img :src="`https://image.tmdb.org/t/p/w342/${img}`" :alt="(img)">

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

}
</script>

<style lang="scss" scoped>

</style>