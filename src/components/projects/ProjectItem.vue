<template>
  <li>
    <h3>{{ title }}</h3>
  </li>
</template>

<script>
export default {
  props: ['title'],
};
</script>

<style lang="scss" scoped>
li {
  padding: 0.5rem;
  margin: 1rem 0;
  color: #35495e;
  background-color: #42b883;

  h3 {
    margin: 0;
  }
}
</style>