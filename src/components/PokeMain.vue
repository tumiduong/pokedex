<template>
  <div class="poke-screen" >
    <div v-if="pokemon.sprites">
      <img :alt='pokemon.name' :src='pokemon.sprites.front_default' />
      <p class="poke-name">{{pokemon.name | capitalize}}</p>
      <div class='poke-types'>
        <div v-bind:key='type.slot' v-for='type of pokemon.types' class='type' v-bind:class='type.type.name'>{{type.type.name | capitalize}}</div>
      </div>
      <div class='poke-stats'>
        <div class='stat' v-bind:key='stat.stat.name' v-for='stat of pokemon.stats'>
          <div class='stat-type'>{{stat.stat.name | statFormat}}</div>
          <div class='stat-value'>{{stat.base_stat}}</div>
        </div>
      </div>
    </div>
  
    <p v-else></p>

  </div>
</template>

<script>
export default {
  name: 'PokeMain',
  props: {
    pokemon: Object
  },
  filters: {
  capitalize: value => {
    return value.charAt(0).toUpperCase() + value.slice(1);
  },
  statFormat: value => {
    const stat = value.replace('-', ' ').replace('special', 'sp').replace('attack', 'atk').replace('defense', 'def');
    return stat.toUpperCase();
  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.poke-screen {
  width: 748px;
  height: 544px;
  position: absolute;
  top: 60px;
  margin: auto;
}

img {
  position: absolute;
  top: 31%;
  left: 27%;
  z-index: 1;
  background-color: rgb(236, 236, 236);
  border-radius: 50px;
  width: 96px;
  height: auto;
  border: lightgray 1px solid;
}

.poke-name {
  font-family: 'Press Start 2P', cursive;
  font-size: 12px;
  position: absolute;
  top: 30%;
  left: 11%;
}

.poke-types {
  font-size: 12px;
  text-align: center;
  position: absolute;
  top: 35%;
  left: 11%;
}

.type {
  margin-top: 5px;
  padding: 3px 15px;
  border-radius: 20px;
}

.grass {
  background-color: rgb(166, 255, 158);
}

.poison {
  background-color: rgb(224, 169, 224);
}

.fire {
  background-color: rgb(253, 180, 95);
}

.flying {
  background-color: rgb(221, 214, 238);
}

.water {
  background-color: rgb(143, 223, 255);
}

.bug {
  background-color: rgb(198, 223, 91);
}

.normal {
  background-color: rgb(214, 209, 193);
}

.electric {
  background-color: rgb(247, 233, 44);
}

.ground {
  background-color: rgb(233, 212, 121);
}

.fairy {
  background-color: rgb(255, 193, 229);
}

.fighting {
  background-color: rgb(255, 102, 102);
}

.rock {
  background-color: rgb(207, 181, 61);
}

.steel {
  background-color: rgb(207, 207, 207);
}

.ice {
  background-color: rgb(198, 239, 255);
}

.ghost {
  background-color: rgb(186, 135, 207);
}

.psychic {
  background-color: rgb(255, 106, 193);
}

.dark {
  background-color: rgb(185, 172, 152);
}

.dragon {
  background-color: rgb(154, 143, 255);
}

.poke-stats {
  font-size: 9px;
  text-align: center;
  position: absolute;
  top: 50%;
  left: 10%;
  display: flex;
}

.stat {
  background-color: lightgray;
  border-radius: 25px;
  padding: 7px 2px;
  margin: 0px 1px;
  width: 31px;
}

.stat-type {
  font-weight: bold;
  margin: 2px 0px 8px 0px;
}

.stat-value {
  font-family: 'Press Start 2P', cursive;
}
</style>
