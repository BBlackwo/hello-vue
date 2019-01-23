<template>
  <ul>
    <li v-for="person in people" v-bind:key="person.name">
      {{ person.name }}
    </li>
  </ul>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import axios from 'axios';

@Component
export default class People extends Vue {
  people = [];

  mounted () {
    axios
      .get('https://swapi.co/api/people/')
      .then(response => (this.people = response.data.results))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
