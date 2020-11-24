<template>
  <form>
    <input type="text" name="pokemon" placeholder="Pokemon ID or name" autocomplete="off" />
    <input type="submit" value="Search" />
  </form>
</template>

<script>
export default {
  name: "PokedexSearch",
  data() {
    return {
      pokemon: ""
    };
  }
};
</script>

<style scoped>

</style>
