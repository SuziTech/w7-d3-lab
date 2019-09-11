<template lang="html">
  <div>
    <select v-model="selected">
      <option v-for="(country, index) in countries"
        :country="country.name" :key="index">
        <span>{{ selected }}</span>        
      </option>
    </select>
  </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'countries-list',
  props: ['countries'],
  components: {
    "option": Option
  }
}
</script>

<style lang="css" scoped>
ul {
  list-style-type: none;
}
</style>
