<script setup>
  import {ref} from "vue"

  let num = ref(0)
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <router-link class="navbar-brand neon-text" to="/">Rick and Morty</router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link class="nav-link active" aria-current="page" to="/">Início</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link active" aria-current="page" to="/about">Sobre</router-link>
        </li>
      </ul>
    </div>
  </div>
</nav>


<div class="main">
  <router-view></router-view>
</div>

<footer class="bg-dark text-light">
  <div>Unimar | ADS | {{ new Date().getFullYear() }}</div>

</footer>
</template>

<style>
.neon-text {
  color: #00f7ff;
  font-family: 'Comic Sans MS', cursive, sans-serif; 
  text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 30px #fff, 0 0 40px rgb(0, 255, 98), 0 0 70px rgb(0, 255, 85), 0 0 80px rgb(0, 255, 64), 0 0 100px rgb(0, 255, 76), 0 0 150px rgb(0, 255, 76);
}

.nav-link {
  color: #00f7ff !important;
}

.navbar-nav .nav-link {
  font-family: 'Comic Sans MS', cursive, sans-serif; 
}
  footer {
    position: fixed;
    bottom: 0;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 15px;
  }
  
</style>