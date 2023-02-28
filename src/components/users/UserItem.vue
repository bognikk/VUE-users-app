<template>
  <li>
    <h3>{{ userName }}</h3>
    <button @click="viewProjects">View Projects</button>
  </li>
</template>

<script>
export default {
  props: ['id', 'userName'],
  emits: ['list-projects'],
  methods: {
    viewProjects() {
      this.$emit('list-projects', this.id);
    },
  },
};
</script>

<style lang="scss" scoped>
li {
  padding: 1rem;
  margin: 1rem 0;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);

  h3 {
    margin: 0;
  }
}
</style>