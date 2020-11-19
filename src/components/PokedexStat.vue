<template>
  <li>
    <span>
      <b>{{ item.stat.name.toUpperCase() }}: </b>
    </span>
    <span>{{ item.base_stat }}</span>
  </li>
</template>

<script>
export default {
  name: "PokedexStat",
  props: {
    item: {
      type: Object,
      default: () => {}
    }
  }
};
</script>

<style scoped>

</style>
