<template lang="html">
  <div class="pokemon-detail" v-if="pokemon">
    <h1>Details of Pokemon</h1>
    <div class="detail-holder">

      <div class="attributes">
        <p>Name: <b> {{pokemon.name.toUpperCase()}}</b> </p>
        <p>Move: <b>{{pokemon.moves[0].move.name}}</b> </p>
        <p>Weight: <b>{{pokemon.weight}}kg</b></p>
        <p class="type-label">Type: </p>
        <p class="type" v-for="type in pokemon.types"><b>{{type.type.name}}</b> </p>
        <p># <b>{{pokemon.id}}</b></p>
      </div>
      <div class="image-container">
        <img :src="pokemon.sprites.front_default" :alt="pokemon.name + ' image'">
      </div>
    </div>

  </div>

</template>

<script>
export default {
  props: ['pokemon']
}
</script>

<style lang="css" scoped>
img {
  width: 100%;
}

.attributes {
  width: 50%;
  padding-left: 60px;
  padding-top: 20px;
}

.image-container {
  border-left: 10px solid red;
  width: 50%;
}

.detail-holder {
  display: flex;
  border: 10px solid red;
  width: 50%;
  border-radius: 10px;
  margin-left: auto;
  margin-right: auto;
  background-color: white;
}

h1 {
  text-align: center;
  background-color: white;
  padding-top: 20px;
  padding-bottom: 20px;
  margin-bottom: 0;
  margin-top: 0;
}

.type {
  display: inline;
  margin-right: 10px;
}

.type-label {
  display: inline;
}

p {
  text-transform: capitalize;
}

.pokemon-detail {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
}
</style>
