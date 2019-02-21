<template lang="html">
  <option v-on:change="handleChange">{{ country.name }}</option>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'list-component',
  props: ['country'],
  methods: {
    handleChange(){
      eventBus.$emit('country-selected', this.country);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
