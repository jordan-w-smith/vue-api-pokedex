<template>
  <div id="app">
    <pokemon-detail :pokemon="selectedPokemon"></pokemon-detail>
    <pokemon-list :pokemons="pokemons"></pokemon-list>
  </div>
</template>

<script>
import {eventBus} from './main.js'
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
    "pokemon-list": PokemonList,
    "pokemon-detail": PokemonDetail
  },
  mounted() {
    fetch('https://pokeapi.co/api/v2/pokemon?limit=500')
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
