<template lang="html">
  <li v-on:onchange="handleChange(country)">{{country.name}}</li>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'option',
  props: ['country'],
  methods:{
    handleChange(country){
      eventBus.$emit('selected', country)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
