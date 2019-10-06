<template lang="html">
  <div class="pokemon-detail" v-if="pokemon">
    <h1>Details of Pokemon</h1>
    <div class="detail-holder">

      <div class="attributes">
        <p>Name: <b> {{pokemon.name.toUpperCase()}}</b> </p>
        <p>Move: <b>{{pokemon.moves[0].move.name}}</b> </p>
        <p>Weight: <b>{{pokemon.weight}}</b> </p>
        <p>Type: <b>{{pokemon.types[0].type.name}}</b> </p>
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
}
</style>
