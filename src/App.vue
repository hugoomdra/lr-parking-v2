<template>

<!-- <h1><img src="./assets/logo-la-rochelle.jpg" style="width: 500px;" alt="LR PARKING"></h1> -->

Test version en ligne

<div v-if="response" v-for="value in response.data.records" style="background-color: #01FFFF; padding: 20px; margin: 10px;">
  <p><span style="font-weight: bold;">{{ value.fields.nom }}</span> : {{ value.fields.nb_places_disponibles }}/{{value.fields.nb_places}}</p>
</div>
<div v-else>
  Si ce message s'affiche, c'est que l'API ne répond pas. Vous pouvez ouvrir la console pour visualiser l'erreur
</div>

<!-- <p>made by mdramedia</p> -->

</template>

<script setup lang="ts">

import axios from 'axios'
import { ref } from 'vue';
import { values } from './data/data'

const url = "https://api.agglo-larochelle.fr/production/opendata/api/records/1.0/search/dataset=parking___places_disponibles_en_temps_reel&facet=id&api-key=2ac2e9a3-3ba3-4d82-b071-0af0c8bac92c"

const response = ref()

async function fetchData() {
    try{
    response.value = await axios.get(url)
  }catch(e){
    console.log(e)
  }
  
}

fetchData();

</script>

<style scoped>

</style>