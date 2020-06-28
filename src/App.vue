<template>
  <div id="app">
    <div class="pokedex">
      <img alt="Pokedex" src="../public/pokedex.png">
      <PokeMain v-bind:pokemon='pokemon'/>
      <PokeInfo v-bind:pokemon='pokemon'/>
      <PokeNumber v-bind:pokemon='pokemon' @id-change="fetchPokemon" />
    </div>
  </div>
</template>

<script>
import Pokedex from 'pokedex-promise-v2';
import PokeMain from './components/PokeMain';
import PokeInfo from './components/PokeInfo';
import PokeNumber from './components/PokeNumber';

const P = new Pokedex();

export default {
  name: 'App',
  components: {
    PokeMain,
    PokeInfo,
    PokeNumber
  },
  data() {
    return {
      pokemon: {}
    }
  },
  created() {
    P.resource('api/v2/pokemon/1')
    .then(response => {
      this.pokemon = response;
      console.log(this.pokemon)
    })
  },
  methods: {
    fetchPokemon: function(id) {
      P.resource(`api/v2/pokemon/${id}`)
      .then(response => {
        this.pokemon = response;
        console.log(this.pokemon)
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Ubuntu', sans-serif;
  margin-top: 60px;
}

.pokedex {
  max-width: 748px;
  margin: auto;
}
</style>
