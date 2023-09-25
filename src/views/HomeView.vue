<script setup>
import { onMounted, ref, computed } from 'vue';
import ListPokemons from '../components/ListPokemons.vue';

let pokemons = ref([]);
let searchTerm = ref('');

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon/?limit=20&offset=0")
  .then(response => response.json())
  .then(response => {
    pokemons.value = response.results;
  })
});

const filteredPokemons = computed(() => {
  const term = searchTerm.value.toLowerCase();
  return pokemons.value.filter(pokemon => pokemon.name.toLowerCase().includes(term));
});
</script>

<template>
  <main>
    <div class="container">
      <div class="row mt-4">
        <div>
          <div class="input-group input-group-sm mb-3">
          <input
            type="text" style="color: black; font-family: Arial; font-weight: bold; border-color: black; padding: 10px; font-size: 20px;"
            class="form-control"
            v-model="searchTerm"
            placeholder="Search"
          />
          </div>
          <div class="card">
            <div class="card-body row" v-if="filteredPokemons.length > 0">
              <ListPokemons
                v-for="pokemon in filteredPokemons"
                :key="pokemon.name"
                :name="pokemon.name"
                :url="pokemon.url"
              />
            </div>
            <div v-else>
              Nenhum Pokémon encontrado.
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style>
.container {
  margin-top: 0%;
}

.card {
  border: none;
}

</style>
