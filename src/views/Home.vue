<template>
  <div>
    <Searchbar
      placeHolderText="Enter Pokemon here"
      @input-searchterm="updateSearchTerm"
    />
    <PokeList :listOfPokemon="filteredListOfPokemon" />
  </div>
</template>

<script>
import { computed, reactive, toRefs } from "vue";
import Searchbar from "@/components/Searchbar.vue";
import PokeList from "@/components/PokeList.vue";

export default {
  name: "Home",
  components: {
    Searchbar,
    PokeList,
  },
  setup() {
    const state = reactive({
      listOfPokemon: [],
      urlIdLookup: {},
      searchterm: "",
      filteredListOfPokemon: computed(() => updateFilteredList()),
    });

    function updateFilteredList() {
      if (state.searchterm.length < 2) {
        return [];
      } else {
        return state.listOfPokemon.filter((pokemon) =>
          pokemon.name.includes(state.searchterm)
        );
      }
    }

    function updateSearchTerm(payLoad) {
      state.searchterm = payLoad.toLowerCase();
    }

    fetch("https://pokeapi.co/api/v2/pokemon?limit=-1")
      .then((response) => response.json())
      .then((data) => {
        state.listOfPokemon = data.results.map((el, index) => ({
          ...el,
          slugNumber: index + 1,
        }));
      });
    return { ...toRefs(state), updateSearchTerm };
  },
};
</script>
