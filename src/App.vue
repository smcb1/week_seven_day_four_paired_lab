<template lang="html">
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <countries-list :countries="countries"></countries-list>
      <country-detail :country="selectedCountry"></country-detail>
    </div>
  </div>
</template>

<script>
import CountriesList from "./components/CountriesList.vue";
import CountryDetail from "./components/CountryDetail.vue";
import {eventBus} from "./main.js";

export default {
  name: 'app',
  data() {
    return {
      countries: [],
      selectedCountry: null
    }
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => {
      this.countries = countries
      this.selectedCountry = this.countries[0]
    })

    eventBus.$on('selected-country', (country) => {
      this.selectedCountry = country;
    })
  }
}
</script>

<style lang="css" scoped>
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
