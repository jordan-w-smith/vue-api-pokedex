<template lang="html">
  <div v-if="pokemon">
    <h1>Details of Pokemon</h1>
    <p>Name: <b> {{pokemon.name}}</b> </p>
    <p>Move <b>{{pokemon.moves[0].move.name}}</b> </p>
  </div>

</template>

<script>
export default {
  props: ['pokemon']
}
</script>

<style lang="css" scoped>
</style>
