<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>Pokemon List</h1>
    <pokemon-detail :pokemon="selectedPokemon"></pokemon-detail>
    <pokemon-list :pokemons="pokemons"></pokemon-list>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import HelloWorld from './components/HelloWorld.vue'
import PokemonList from './components/PokemonList.vue'
import PokemonDetail from './components/PokemonDetail.vue'

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
    "pokemon-list": PokemonList,
    "pokemon-detail": PokemonDetail
  },
  mounted() {
    fetch('https://pokeapi.co/api/v2/pokemon?limit=150')
    .then(res => res.json())
    .then(pokemons => this.pokemons = pokemons)

    eventBus.$on('pokemon-selected', pokemon => this.getPokemonDetails(pokemon.name) )
  },
  methods: {
    getPokemonDetails: function(pokemonName) {
      fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonName}`)
        .then(res => res.json())
        .then(pokemon => this.selectedPokemon = pokemon)
    }
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
