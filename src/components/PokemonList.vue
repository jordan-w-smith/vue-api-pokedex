<template lang="html">
  <ul>
    <list-item v-for="pokemon in pokemons" :pokemon="pokemon"></list-item>
  </ul>
</template>

<script>
import ListItem from './ListItem.vue'
export default {
  props: ["pokemons"],
  components: {
    "list-item": ListItem
  }
}
</script>

<style lang="css" scoped>
</style>
