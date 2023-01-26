<script setup> 
import {useRoute, useRouter} from 'vue-router'
import { useGetData } from '../composables/getData';
import {useFavoritosStore} from '../store/favoritos.js'
import { storeToRefs } from 'pinia';


const route = useRoute()
const router = useRouter()

const useFavoritos = useFavoritosStore()

const {add, findPoke} = useFavoritos


const back = () => {
    router.push('/pokemons')
}

const {data, getData, loading, error} = useGetData()

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)


</script>


<template>
    <p v-if="loading"> Cargando info</p>
    <div class="alert alert-danger mt-2" v-if="error">No existe el pokemon </div>
    <div v-if="data">
        <img :src="data.sprites?.other.home.front_default" height="150" width="150">
         <h1>Poke name: {{ $route.params.name }}</h1>
         <button :disabled="findPoke(data.name)" class="btn btn-primary mb-2" @click="add(data)"> Agregar favoritos</button>
    </div>

   
    <button @click="back" class="btn btn-info"> back</button>
</template>