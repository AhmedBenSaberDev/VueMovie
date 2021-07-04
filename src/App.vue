<template>
  <div class="app">
    <header>
      <router-link to="/">
        <h1>Vue<span>Movies</span> </h1>
      </router-link>
    </header>

    <main>
      <router-view />
    </main>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;500&display=swap');
*{
  padding:0;
  margin: 0;
  box-sizing: border-box;
  font-family: poppins;
}
body{
  background-color:#35495E;
}
header{
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 50px;
  background-color: #2C3D4E;  
  box-shadow: rgba0 0px 0px 6px (0,0,0,0.1);
}
a{
  text-decoration: none;
}
h1{
  color: white;
  font-size: 30px;
}
span{
  color: #42b883;
}
</style>
