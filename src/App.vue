<template>

<h1><img src="./assets/logo-la-rochelle.jpg" style="width: 500px;" alt="LR PARKING"></h1>


<div v-for="value in response.data.records" style="background-color: #01FFFF; padding: 20px; margin: 10px;">
  <p v-if="response" ><span style="font-weight: bold;">{{ value.fields.nom }}</span> : {{ value.fields.nb_places_disponibles }}/{{value.fields.nb_places}}</p>
</div>

<p>made by mdramedia </p>

</template>

<script setup lang="ts">

import axios from 'axios'
import { ref } from 'vue';
import { values } from './data/data'

const url = "https://api.agglo-larochelle.fr/production/opendata/api/records/1.0/search/dataset=parking___places_disponibles_en_temps_reel&facet=id"

const env = "TEST"


const response = ref()

async function fetchData() {
  if(env === "TEST") {
    response.value = {
      data: {...values}
    }
  } else {
    try{
    response.value = await axios.get(url, {
      headers: {
      "Access-Control-Allow-Origin": "*",
      "Access-Control-Allow-Methods": "GET,PUT,POST,DELETE,PATCH,OPTIONS",
      'Access-Control-Allow-Credentials':true,
    }
  })
  }catch(e){
    console.log(e)
  }
  }  
}

  

fetchData();

</script>

<style scoped>

</style>