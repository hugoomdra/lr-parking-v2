<template>

<h1>LR Parking</h1>

</template>

<script setup lang="ts">

import axios from 'axios'

const url = "https://api.agglo-larochelle.fr/production/opendata/api/records/1.0/search/dataset=parking___places_disponibles_en_temps_reel&facet=id"


async function fetchData() {
  try{
    const response = await axios.get(url, {
      headers: {
      "Access-Control-Allow-Origin": "*",
      "Access-Control-Allow-Methods": "GET,PUT,POST,DELETE,PATCH,OPTIONS",
      'Access-Control-Allow-Credentials':true,
    }
  })
  console.log(response.data)
  }catch(e){
    console.log(e)
  }
  
}

fetchData();

</script>

<style scoped>

</style>