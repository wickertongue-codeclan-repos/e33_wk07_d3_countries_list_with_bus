<template>
  
  <article v-if="country">
    <h3>You have selected: {{country.name}}</h3>
    <p>Native name: {{country.nativeName}}</p>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
  </article>

</template>

<script>

export default {
  name: 'country-detail',
  props: ['country']
}

</script>

<style>

</style>