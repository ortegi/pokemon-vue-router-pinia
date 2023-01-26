<script setup>
    import {useFavoritosStore} from '../store/favoritos.js'
    import { storeToRefs } from 'pinia';
    import {RouterLink} from 'vue-router'
    const useFavoritos = useFavoritosStore()


    const {favoritos} = storeToRefs(useFavoritos)
    const {byePokemon} = useFavoritos
</script>


<template>
    <h1>Favoritos</h1>
    <p v-if="favoritos.length === 0"> Sin Favoritos</p>
    <ul class="list-group">
        <li class="list-group-item" 
         v-for="fav in favoritos"
        :key="fav.id">
           <div>
            {{ fav.name }}
           </div>
           <div>
                <button class="btn btn-danger bt-sm" @click="byePokemon(fav.id)">Eliminar </button>
                <router-link class="btn btn-outline-primary" :to="`/pokemons/${fav.name}`"> Mas info </router-link>
           </div>
        </li>
    </ul>
</template>