<template>
  <div class="w-full flex justify-center">
    <input
      type="text"
      :placeholder="placeHolderText"
      class="mt-10 p-2 border-blue-500 border-2"
      v-on:input="$emit('input-searchterm', $event.target.value)"
    />
  </div>
</template>

<script>
export default {
  name: "Searchbar",
  props: {
    placeHolderText: {
      type: String,
      required: true,
    },
  },
};
</script>

<style></style>
