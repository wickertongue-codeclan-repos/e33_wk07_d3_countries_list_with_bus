<template>
  
  <div>
    <h1>This is a Heading</h1>
      <div>
        <select id="selectedCountry">
          <option v-for="(country, index) in countries" v-bind:value="index">
            {{country.name}}
          </option>
        </select>
        <country-detail :country="selectedCountry"></country-detail>
      </div>
  </div>

<!-- v-model 

v-onchange -->

</template>

<script>
import CountryDetail from './components/CountryDetail.vue';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data() {
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted() {
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country
    })
  },
  components: {
    "country-detail": CountryDetail
  }
}



</script>

<style>

</style>