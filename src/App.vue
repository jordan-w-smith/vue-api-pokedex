<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>Pokemon List</h1>
    <pokemon-list :pokemons="pokemons"></pokemon-list>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import HelloWorld from './components/HelloWorld.vue'
import PokemonList from './components/PokemonList.vue'

export default {
  name: 'app',
  data() {
    return {
      pokemons: [],
      selectedPokemon: null
    }
  },
  components: {
    HelloWorld,
    "pokemon-list": PokemonList
  },
  mounted() {
    fetch('https://pokeapi.co/api/v2/pokemon?limit=150')
    .then(res => res.json())
    .then(pokemons => this.pokemons = pokemons)
  },
  methods: {
    // eventBus.$on('pokemon-selected', (pokemon) => {
    //   this.selectedPokemon = pokemon
    // })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
