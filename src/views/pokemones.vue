<script setup>
import {RouterLink} from 'vue-router'
import {useGetData} from '@/composables/getDatos'

const {data,getData,loading,errorData}=useGetData();
getData('https://pokeapi.co/api/v2/pokemon/');
</script>
<template>
    <h1>Pokemones</h1>
    <p v-if="loading">Cargando informacion..</p>
    <div class="alert alert-danger" v-if="errorData">{{errorData}}</div>
    <div v-if="data">
        <ul class="list-group">
            <li class="list-group-item" v-for="pokem in data?.results">
                <router-link :to="`/pokemones/${pokem.name}`">{{pokem.name}}</router-link>
            </li>
        </ul>
        <div class="mt-2">
            <button :disabled="!data.previous"
            class="button btn btn-success me-2" 
            @click="getData(data.previous)">
            Previous
            /button>
            button :disabled="!data.next" class="button btn btn-primary" 
            click="getData(data.next)">
            ext</button>
        </div>
        
    </div>
 </template>