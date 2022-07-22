<template>
  <div class="container">
    <div class="input-group my-3">
      <input type="text" class="form-control" placeholder="Search..." aria-label="Search" aria-describedby="basic-addon1" v-model.trim="getSearchItem" @keypress.enter="$emit('search', getSearchItem.toLowerCase())">
    </div>
    <button class="btn btn-primary m-3" @click="$emit('search', getSearchItem.toLowerCase())">Search</button>
    
  </div>
</template>

<script>
export default {
  
  data: function(){
    return{
      getSearchItem: '',
    }
  },
  methods: {

  

    

  }

}
</script>

<style lang="scss" scoped>




</style>