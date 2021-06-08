<template>
  <div class="ml-4 text-2xl text-blue-500">
    <router-link :to="`/about/${pokemon.slugNumber}`">
      {{ pokemon.name }}
    </router-link>
  </div>
</template>

<script>
export default {
  name: "ListElement",
  props: {
    pokemon: {
      type: Object,
      required: true,
      default: () => {},
    },
  },
  components: {},
};
</script>

<style>
</style>