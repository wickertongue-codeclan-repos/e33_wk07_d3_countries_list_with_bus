<template>
  
  <div>
    <h1>This is a Heading</h1>
      <div>
        <country-detail :country="selectedCountry"></country-detail>
        <countries-list :countries="countries"></countries-list>
      </div>
  </div>

</template>

<script>
import CountryDetail from './components/CountryDetail.vue';
import CountriesList from './components/CountriesList.vue';
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
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }
}



</script>

<style>

</style>