<template lang="html">
  <li v-on:click="handleClick"># {{pokemon.name}}</li>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  props: ['pokemon'],
  methods: {
    handleClick() {
      eventBus.$emit('pokemon-selected', this.pokemon)
    }
  }
}
</script>

<style lang="css" scoped>
li:hover {
  color: red;
  cursor: pointer;
}

li {
  color: black;
  text-decoration: none;
  font-size: 30px;
  text-transform: capitalize;

}

li {
  margin-bottom: 10px;
  list-style-type: none;
}
</style>
