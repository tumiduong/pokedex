<template>
  <div class="poke-info" >
    <div v-if="pokemon.abilities">
      <div class='poke-abilities'>
          Abilities:
        <div v-bind:key='ability.slot' v-for='ability of pokemon.abilities' class='abilities'>{{ability.ability.name | capitalize}}</div>
      </div>
    </div>
  
    <p v-else></p>

  </div>
</template>

<script>
export default {
  name: 'PokeInfo',
  props: {
    pokemon: Object
  },
  filters: {
  capitalize: value => {
    return value.charAt(0).toUpperCase() + value.slice(1);
  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.poke-info {
  width: 748px;
  height: 544px;
  position: absolute;
  top: 60px;
  margin: auto;
}

.poke-abilities {
  font-family: 'Press Start 2P', cursive;
  font-size: 10px;
  color: white;
  position: absolute;
  top: 35%;
  left: 61%;
}

.abilities {
    margin: 3px 0px;
}
</style>
