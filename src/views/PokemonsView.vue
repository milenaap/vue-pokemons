<script setup>

import axios from 'axios';
import { ref } from 'vue';
import {RouterLink} from 'vue-router';

const pokemons = ref([])

const getData = async () =>{
    try {
        const {data} = await axios.get('https://pokeapi.co/api/v2/pokemon/')
        pokemons.value = data.results 
        //console.log(pokemons);
    } catch (error) {
       
    }
}

getData();


</script>



<template>
<h1>Pokemons</h1>
<ul>
    <li  
        v-for = "pokemon in pokemons"
        :key="pokemon.name"
    >
    <router-link :to="`/pokemons/${pokemon.name}`">
        {{pokemon.name}}
    </router-link>
    </li>
</ul>




</template>




<style>





</style>