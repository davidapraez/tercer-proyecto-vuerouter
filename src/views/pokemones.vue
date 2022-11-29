<script setup>

//import axios from 'axios'
import {ref} from 'vue'
import {RouterLink} from 'vue-router'
const pokemons=ref([])
const getData=async()=>{
    try{
        const res=await fetch('https://pokeapi.co/api/v2/pokemon/')
        const data=await res.json()
        pokemons.value=(data.results)
    }catch(error){
        console.log(error);
    }
}
getData()

</script>

<template>
    <h1>Pokemones</h1>
    <ul>
        <li v-for="pokem in pokemons">
            <router-link :to="`/pokemones/${pokem.name}`">{{pokem.name}}</router-link>
                
        </li>
    </ul>

</template>