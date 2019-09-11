<template>
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <country-detail :country="selectedCountry"></country-detail>
      <countries-list :countries='countries'></countries-list>
    </div>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selected: ''
    };
  },
  mounted(){
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
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
