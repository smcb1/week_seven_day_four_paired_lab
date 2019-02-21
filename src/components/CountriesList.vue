<template lang="html">
  <div>
    <select v-on:change="handleChange" v-model="selectedCountryIndex">
      <option v-for="(country, index) in countries" :value="index">{{ country.name }}</option>
    </select>
  </div>

</template>

<script>
import ListComponent from './ListComponent.vue';
import {eventBus} from '../main.js';

export default {
  name: 'countries-list',
  props: ['countries'],
  data() {
    return{
      selectedCountryIndex: 0
    }
  },
  methods: {
    handleChange() {
      eventBus.$emit('selected-country', this.countries[this.selectedCountryIndex]);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
