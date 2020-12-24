<template>
  <form v-on:submit="handleSubmit" class="search-form">
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

<style scoped>
.search-form {
  margin: 0 0 30px 0;
  box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.5);
  transition: 0.3s;
}

.search-form:hover {
  box-shadow: 0 10px 18px 0 rgba(0, 0, 0, 0.5);
}

.search-form > input[type="text"] {
  padding: 10px;
  border-radius: 5px 0 0 5px;
  border: none;
}

.search-form > input[type="submit"] {
  padding: 10px;
  border-radius: 0 5px 5px 0;
  border: none;
}
</style>
