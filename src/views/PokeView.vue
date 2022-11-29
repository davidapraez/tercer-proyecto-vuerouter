<script setup>
import {ref} from 'vue'
import {useRoute,useRouter} from 'vue-router'

const route=useRoute();
const router=useRouter();
const poke=ref({})

const back=async()=>{
        router.push('/pokemones')
}
const getData=async()=>{
    try{
        const res=await fetch(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
        const data= await res.json()
        console.log(data);
        poke.value=data
    }catch(error){
        console.log(error);
        poke.value=null;
    }
}

getData();
</script>

<template>
    <div v-if="poke">
        <img :src="poke.sprites?.front_default" alt="#" class="imgn">
        <h1>Poke name: {{$route.params.name}}</h1>
        <h4>abilities</h4>
        <ul>
            <li v-for="hability in poke.abilities">
                {{hability.ability.name}}
            </li>
        </ul>


    </div>
    <h1 v-else>No existe el Poke</h1>
    <button @click="back" class="btn btn-outline-primary ">Volver</button>
</template>

<style>
.imgn{
    display: block;
    margin: auto;
}
</style>