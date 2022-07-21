<template>
  <div id="app">
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data: function(){
    return{
      apiSrcUrl: 'https://api.themoviedb.org/3/search/movie?api_key=5ff24ba7734ff867e412b5136fda3d11&query=ritorno+al+futuro'
    }
  },
  methods: {
    getApiRequest(){
      axios.get(this.apiSrcUrl)
      .then((results) => {
        console.log(results.data.results);
      })
    }
  },
  created(){
    this.getApiRequest()
  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss'
</style>
