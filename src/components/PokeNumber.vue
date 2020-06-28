<template>
  <div class="poke-number" >
    <div v-if="pokemon.id" class='poke-id'>
        #<input :value='pokemon.id | formatNumber' maxlength="3">
    </div>
  
    <p v-else></p>

  </div>
</template>

<script>
export default {
  name: 'PokeNumber',
  props: {
    pokemon: Object
  },
  filters: {
      formatNumber: value => {
          if (value.toString().length < 3) {
              return ('00' + value.toString()).slice(-3);
          } else {
              return value;
          }
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.poke-number {
  width: 748px;
  height: 544px;
  position: absolute;
  top: 60px;
  margin: auto;
}

.poke-id {
  font-family: 'Press Start 2P', cursive;
  font-size: 20px;
  position: absolute;
  top: 85%;
  left: 12%;
}

input {
    background: none;
    outline: none;
    border: none;
    font-family: 'Press Start 2P', cursive;
    font-size: 20px;
    width: 18%;
    margin-left: 10px;
}
</style>
