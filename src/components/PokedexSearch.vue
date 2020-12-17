<template>
  <form v-on:submit="handleSubmit">
    <input
      type="text"
      name="pokemon"
      placeholder="Pokemon ID or name"
      autocomplete="off"
      v-model="pokemonId"
    />
    <input
        type="submit"
        value="Search"
        v-on:click="searchPokemon"
    />
  </form>
</template>

<script>
export default {
  name: "PokedexSearch",
  data() {
    return {
      pokemonId: ""
    };
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
    },
    searchPokemon(e) {
      e.preventDefault();
      const pokemonId = this.pokemonId;
      const newPokemonId = window.isNaN(parseInt(pokemonId))
        ? pokemonId.toLowerCase()
        : pokemonId;
      this.$emit("submit", newPokemonId);
    }
  }
};
</script>

<style scoped></style>
