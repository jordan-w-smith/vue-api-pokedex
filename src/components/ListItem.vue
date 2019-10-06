<template lang="html">
  <li v-on:click="handleClick">{{pokemon.name}}</li>
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
</style>
