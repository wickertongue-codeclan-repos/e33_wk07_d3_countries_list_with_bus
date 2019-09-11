<template>
  
  <div>
    <h3>List of Countries</h3>
      <div>
        <list-component v-for="(country, index) in countries" :country="country" :key="index"></list-component>
      </div>
  </div>

</template>

<script>

import ListComponent from './ListComponent.vue';

export default {
  name: 'countries-list',
  props: ['countries'],
  components: {
    "list-component": ListComponent
  }
}

</script>



<style>
</style>