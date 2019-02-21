<template lang="html">
  <div v-if="country">
    <h1>Country: {{ country.name }}</h1>
    <p>Capital: {{ country.capital }}</p>
    <p>Region: {{ country.region }}</p>
    <p>Pop: {{ country.population }}</p>
  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
</style>
