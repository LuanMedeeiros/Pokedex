<script setup>
import {ref} from 'vue'

let num = ref(0)

</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container-fluid">
      <router-link to="/" class="navbar-brand" style="pointer-events: none;"><strong>Pokedex | Vue.js</strong></router-link>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link to="/" class="nav-link" aria-current="page"><strong>Home</strong></router-link>
          </li>
          <li class="nav-item">
            <router-link to="/about" class="nav-link"><strong>About the project</strong></router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
 
  <div class="main">
    <router-view></router-view>
  </div>

  <footer class="bg-dark text-light">
    <div><strong>Unimar | ADS | {{ new Date().getFullYear() }}</strong></div>
  </footer>

</template>

<style>
footer{
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 50px;
}

.main{
  margin-top: 110px;
  margin-bottom: 100px;
  margin-left: 10%;
  margin-right: 10%;
}

.direita {
  margin-right: flex;
  margin-top: 1%;
}

</style>