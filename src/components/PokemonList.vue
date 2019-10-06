<template lang="html">
  <div>


    <h1>Pokemon List</h1>
    <ul>
      <list-item v-for="pokemon in pokemons.results" :pokemon="pokemon"></list-item>
    </ul>
  </div>
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
