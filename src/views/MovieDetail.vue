<template>
  <div class="movie-detail">
    <div class="movie-detail">
    <h2>{{ $route.params.movieName }}</h2>
    <p>{{ $route.params.movieYear }}</p>
    <img :src="imgPath +'//' + $route.params.movieImg" alt="Movie Poster" class="featured-img" />
    <p>{{ $route.params.movieDesc }}</p>
  </div>
  </div>
</template>

<script>

export default {
  data(){
    return{
      imgPath:'https://image.tmdb.org/t/p/w500',
      searchUrl : 'https://api.themoviedb.org/3/search/movie?api_key=ee58e73e99cf0fb8cc3ded0d80f4e990&query=',
      movie:{},
      movies:[]
    }
  },
}
</script>

<style scoped>
.movie-detail {
  padding: 16px;
}
  h2 {
    color: #FFF;
    font-size: 28px;
    font-weight: 600;
    margin-bottom: 16px;
  }
  .featured-img {
    display: block;
    max-width: 200px;
    margin-bottom: 16px;
  }
  p {
    color: #FFF;
    font-size: 18px;
    line-height: 1.4;
  }
  h2 {
    color: #FFF;
    font-size: 28px;
    font-weight: 600;
    margin-bottom: 16px;
  }
  .featured-img {
    display: block;
    max-width: 200px;
    margin-bottom: 16px;
  }
  p {
    color: #FFF;
    font-size: 18px;
    line-height: 1.4;
  }
</style>