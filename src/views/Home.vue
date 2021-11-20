<template>

  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/ttt45258">
      <img src="https://www.hipandtrippy.com/word/wp-content/uploads/2013/01/The-Avengers-Wallpaper-HD.jpg" alt="avengers" class="featured-img">
      <div class="detail">
        <h3>Avengers</h3>
        <p>Marvel's The Avengers (classified under the name Marvel Avengers Assemble in the United Kingdom and Ireland),[3][7] or simply The Avengers, is a 2012 American superhero film based on the Marvel Comics superhero team of the same name. Produced by Marvel Studios and distributed by Walt Disney Studios Motion Pictures,[N 1] it is the sixth film in the Marvel Cinematic Universe (MCU). Written and directed by Joss Whedon, the film features an ensemble cast including Robert Downey Jr., Chris Evans, Mark Ruffalo, Chris Hemsworth, Scarlett Johansson, and Jeremy Renner as the Avengers, alongside Tom Hiddleston, Clark Gregg, Cobie Smulders, Stellan Skarsgård, and ...</p>
      </div>
      </router-link>
    </div>
    <form @submit.prevent="searchMovie"  class="search-box">
      <input v-model="search" class="text" type="text" placeholder="search your favorite movie">
      <input class="submit-btn"  type="submit" value="search">
    </form>

    <div class="movies-list">
      <div v-show="results">
        <p>no result found for {{ lastSearch }}</p>
      </div>
      <div class="movie" v-for="movie in movies" :key="movie.id" >
        <router-link :to="'/movie/' + movie.title +'/' + movie.release_date + '/' +  movie.poster_path.slice(1,movie.poster_path.length) + '/' + movie.overview" class="movie-link">
          <div class="product-image">
            <img :src="imgPath + movie.poster_path" alt="Movie Poster" />
            <div class="type">{{  }}</div>
          </div>
          <div class="movie-detail">
            <p class="y">{{ movie.release_date }}</p>
            <h3>{{ movie.title }}</h3>
          </div>
        </router-link>
      </div>
    </div>

  </div>
</template>

<script>

export default {
  data(){
    return{
      results:false,
      search:'',
      lastSearch:'',
      imgPath:'https://image.tmdb.org/t/p/w500',
      movies:[],
      searchUrl : 'https://api.themoviedb.org/3/search/movie?api_key=ee58e73e99cf0fb8cc3ded0d80f4e990&query='
    }
  },
  methods:{
    searchMovie()
    {
      if(this.search != '')
      {
        fetch(this.searchUrl + this.search)
        .then(res => res.json())
        .then(data => {
          if(data.results.length != 0){
            this.movies = data.results;
            this.search = '';
            this.results = false
          }else{
            this.lastSearch = this.search;
            this.search = '';
            this.results = true;
          }
            
        })
      }
    }
  }
}
</script>

<style scoped>
.feature-card{
  position:relative;
}
.featured-img{
  display:block;
  width: 100%;
  height: 300px;
  object-fit:cover;
  object-position:0 -100px;
  position:relative;
  z-index: 0;
}
.detail{
  position:absolute;
  right:0;
  bottom: 0;
  left: 0;
  background-color: rgba(0,0,0,0.6);
  padding:16px;
  z-index: 1;
}
h3{
  color:white;
  margin-bottom: 16px;
}
p{
  color:#fff;
}
.search-box{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding:16px;
}
input{
  outline: none;
  border:none;
  appearance: none;
  background: none;
}
.text{
   width: 100%;
   color:#fff;
   background-color: #496583;
   font-size: 20px;
   padding:10px 16px;
   border-radius: 8px;
   margin-bottom: 15px;
   transition:0.4s;
}
::placeholder{
  color:#f3f3f3;
}
:focus{
  box-shadow: 0 3px 6px rgba(0,0,0,0.2);
}
.submit-btn{
  width:100%;
  max-width: 300px;
  background-color: #42b883;
  padding:16px;
  border-radius:8px;
  color:#fff;
  font-size: 20px;
  transition: 0.4s;
  text-transform: uppercase;
  }

.submit-btn:active{
  background-color: #3b8070;
}

.movies-list {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  margin: 0px 8px;
}
.movies-list .movie {
  max-width: 30%;
  flex: 1 1 50%;
  padding: 16px 8px;
}
.movie-link {
  display: flex;
  flex-direction: column;
  height: 100%
}

.movies-list .product-image {
  position: relative;
  display: block;
}
.movies-list img {
  display: block;
  width: 100%;
  height: auto;
  object-fit: cover;
}
.movie-detail {
  background-color: #496583;
  padding: 16px 8px;
  flex: 1 1 100%;
  border-radius: 0px 0px 8px 8px;
}
.year{
  color: #AAA;
  font-size: 14px;
}
.movies-list h3 {
  color: #FFF;
  font-weight: 600;
  font-size: 18px;
}
</style>
