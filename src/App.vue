<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>

  <nav class="navbar navbar-dark bg-dark">
    <div class="container-fluid">
     
      <router-link class="navbar-brand" to="/">
        <img src="@/assets/logo.svg" alt="" width="30" height="24" class="d-inline-block align-text-top">
        PokeAPI
      </router-link>

      <div>
        <router-link to="/" class="btn btn-outline-primary"> Home</router-link>
        <router-link to="/pokemons" class="btn btn-outline-primary"> Pokemons</router-link>
        <router-link to="/favoritos" class="btn btn-outline-primary">favoritos </router-link>
      </div>
    </div>
  </nav>
  <div class="container text-center">  
    
    <RouterView />
    
  </div>

</template>

<style scoped>

</style>
