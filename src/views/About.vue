<template>
  <div class="about">
    <DetailView :pokemon="pokemon" />
  </div>
</template>
<script>
import { useRoute } from "vue-router";
import { reactive, toRefs } from "vue";
import DetailView from "@/components/DetailView.vue";

export default {
  name: "About",
  props: {},
  components: {
    DetailView,
  },

  setup() {
    const route = useRoute();

    const state = reactive({
      pokemon: null,
    });

    fetch(`https://pokeapi.co/api/v2/pokemon/${route.params.slug}`)
      .then((response) => response.json())
      .then((data) => {
        state.pokemon = data;
      });
    return { ...toRefs(state) };
  },
};
</script>

<style></style>
