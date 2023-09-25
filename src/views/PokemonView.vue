<script setup>
import { onMounted, reactive, ref } from 'vue';
import Pokemon from '../components/Pokemon.vue';

let pokemons = reactive(ref());

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon/?limit=20&offset=0")
  .then(response => response.json())
  .then(response => {
    pokemons.value = response.results;
  })
})
</script>

<template>
  <main>   
    <div class="text-center">
      <Pokemon 
      v-for="pokemon in pokemons"
      :key="pokemon.name"
      :name="pokemon.name"
      :url="pokemon.url"/>
    </div>
  </main>
</template>