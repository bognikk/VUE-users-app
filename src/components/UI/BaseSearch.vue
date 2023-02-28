<template>
  <form>
    <input type="search" @input="search" :value="searchTerm" placeholder="Filter items" />
  </form>
</template>

<script>
export default {
  props: ['searchTerm'],
  emits: ['search'],
  methods: {
    search(event) {
      this.$emit('search', event.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
input {
  display: block;
  max-width: 100%;
  width: 100%;
  margin: 0.5rem 0;
  padding: 0.5rem;
  border-radius: 5px;
  border: 1px solid #ccc;
  font: inherit;

  &:focus {
    border-color: #42b883;
    background-color: #d3ffeb;
  }

  &:focus-visible {
    outline-color: #42b883 !important;
  }
}
</style>