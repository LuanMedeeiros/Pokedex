<script setup>
const pokemon = defineProps(["name", "url"]);
const resultado = pokemon.url.split("/");
const index = resultado[6];

VanillaTilt.init(document.querySelectorAll(".col-3"));
</script>

<template id="form">
  <div class="col-3">
    <div class="card h-100 custom-card">
      <div class="card h-100">
        <img :src="`https://raw.githubusercontent.com/PokeApi/sprites/master/sprites/pokemon/other/dream-world/${index}.svg`" alt="Responsive image"/>
      </div>      

      <div class="text-center">
        <h5 class="card-title">{{ pokemon.name.charAt(0).toUpperCase() + pokemon.name.slice(1) }}</h5>
        <router-link :to="{ name: 'pokemonId', params: { id: index }}" type="button" class="btn btn-dark" style="margin: auto"><strong>Inspect</strong></router-link>
      </div>

    </div>
  </div>
</template>

<style>
  .col-3 {
    margin-bottom: 30px;
  }
  .custom-card {
    background-color: white;
    border: 5px solid black;
    border-radius: 16px;
  }

  .custom-card .card-header {
    color: white;
  }

</style>