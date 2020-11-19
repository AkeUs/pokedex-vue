<template>
  <div>
    <h2>{{ pokemon.name }}</h2>
    <img v-bind:src="pokemon.sprites.front_default" v-bind:alt="pokemon.name" />
    <ul>
      <pokedex-stat
        v-for="item in pokemon.stats"
        v-bind:item="item"
        v-bind:key="item.stat.name"
      />
    </ul>
  </div>
</template>

<script>
import PokedexStat from "@/components/PokedexStat";

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

</style>
