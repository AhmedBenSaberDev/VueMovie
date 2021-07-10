<template>
  <div class="movie-detail">
      <h1>detail :{{ $route.params.id }}</h1>
  </div>
</template>

<script>

export default {
  data(){
    return{
      imgPath:'https://image.tmdb.org/t/p/w500',
      searchUrl : 'https://api.themoviedb.org/3/search/movie?api_key=ee58e73e99cf0fb8cc3ded0d80f4e990&query='
    }
  },
  created(){
    fetch(this.searchUrl + this.$route.params.movieName)
    .then(res => res.json())
    .then(data => console.log(data.results))
  }
  
}
</script>

<style>

</style>