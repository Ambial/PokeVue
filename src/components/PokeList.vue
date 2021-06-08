<template>
  <div class="mt-10 p-4 flex flex-wrap justify-center">
    <ListElement
      v-for="(pokemon, index) in listOfPokemon"
      :key="index"
      :pokemon="pokemon"
    />
  </div>
</template>

<script>
import ListElement from "@/components/ListElement.vue";

export default {
  name: "PokeList",
  props: {
    listOfPokemon: {
      type: Array,
      required: true,
      default: () => [],
    },
  },
  components: {
    ListElement,
  },
};
</script>

<style>
</style>