<script setup>
import {RouterLink} from 'vue-router'
import {useGetData} from '@/composables/getDatos'

const {data,getData,loading}=useGetData();
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