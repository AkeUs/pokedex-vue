<template>
  <h2 class="text-help" v-if="error">Error</h2>
  <h2 class="text-help" v-else-if="loading">Espere...</h2>
  <div class="pokedex-card" v-else>
    <div class="pokedex-card-header">
      <h2>{{ pokemon.name.toUpperCase() }}</h2>
      <h3><span class="pokemon-type" v-for="type in pokemon.types" v-bind:key="type.slot">{{ type.type.name }}</span></h3>
    </div>
    <div class="pokedex-card-info">
      <img
        v-bind:src="pokemon.sprites.front_default"
        v-bind:alt="pokemon.name"
      />
      <ul class="pokemon-stats">
        <pokedex-stat
          v-for="item in pokemon.stats"
          v-bind:item="item"
          v-bind:key="item.stat.name"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import PokedexStat from "./PokedexStat";

export default {
  name: "PokedexCard",
  components: {
    PokedexStat
  },
  props: {
    pokemon: {
      type: Object,
      default: () => {}
    },
    loading: {
      type: Boolean,
      default: () => false
    },
    error: {
      type: Boolean,
      default: () => false
    }
  }
};
</script>

<style scoped>
.pokedex-card {
  background-color: #FFFFFF;
  max-width: 600px;
  padding:10px;
  border-radius: 5px;
  box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.5);
  transition: 0.3s;
}

.pokedex-card:hover {
  box-shadow: 0 10px 18px 0 rgba(0, 0, 0, 0.5);
}

.pokedex-card-header {
  text-align: center;
}

.pokedex-card-info {
  display: flex;
  flex-direction: row;
}

.pokemon-stats {
  list-style: none;
}

.text-help {
  color: #FFFFFF;
  font-size: 24px;
}

.pokemon-type {
  background-color: #cfd8dc;
  border-radius: 5px;
  padding: 2px 30px 2px 30px;
  margin: 5px;
}
</style>
