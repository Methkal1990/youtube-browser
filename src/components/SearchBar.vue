<template>
  <div>
    <input type="text" placeholder="Search Videos" @input="updateSearch" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    updateSearch(event) {
      this.$emit("updateSearch", event.target.value);
    },
  },
};
</script>

<style scoped>
input {
  width: 75%;
}
div {
  text-align: center;
  margin: 20px;
}
</style>
