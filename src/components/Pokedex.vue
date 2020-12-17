<template>
  <div>
    <h1>Poked&eacute;x</h1>
    <pokedex-search v-on:submit="handleSubmit($event)" />
    <pokedex-card
      v-bind:pokemon="pokemon"
      v-bind:loading="loading"
      v-bind:error="error"
    />
  </div>
</template>

<script>
import PokedexSearch from "./PokedexSearch";
import PokedexCard from "./PokedexCard";

export default {
  name: "Pokedex",
  components: {
    PokedexCard,
    PokedexSearch
  },
  data() {
    return {
      error: false,
      loading: true,
      pokemon: null,
      pokemonId: Math.floor(Math.random() * 151)
    };
  },
  methods: {
    async getPokemonById() {
      await fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemonId}`)
        .then(response => response.json())
        .then(data => {
          this.pokemon = data;
          this.loading = false;
          this.error = false;
        })
        .catch(err => {
          console.error(err);
          this.loading = false;
          this.error = true;
        });
    },
    handleSubmit(pokemonId) {
      if (pokemonId !== "") {
        this.error = false;
        this.loading = true;
        this.pokemonId = pokemonId;
        this.getPokemonById();
        return;
      }
      this.error = true;
    }
  },
  created() {
    this.getPokemonById();
  }
};
</script>

<style scoped></style>
