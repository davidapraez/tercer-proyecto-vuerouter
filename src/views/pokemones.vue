<script setup>
import {ref} from 'vue'
import {RouterLink} from 'vue-router'
import {useGetData} from '@/composables/getdata'

const {data,getData,loading}=useGetData();
const pokemons=ref([])
getData('https://pokeapi.co/api/v2/pokemon/');

</script>

<template>
    <h1>Pokemones</h1>
    <p v-if="loading">Cargando informacion..</p>
    <div v-if="data">
        <ul >
            <li v-for="pokem in data?.results">
                <router-link :to="`/pokemones/${pokem.name}`">{{pokem.name}}</router-link>
            </li>
        </ul>
    </div>
    

</template>