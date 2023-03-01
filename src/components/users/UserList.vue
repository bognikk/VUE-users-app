<template>
  <base-container>
    <h2>Active Users</h2>
    <base-search @search="updateSearch" :search-term="enteredSearchTerm"></base-search>
    <div>
      <button @click="sort('asc')" :class="{ selected: sorting === 'asc' }">Sort Ascending</button>
      <button @click="sort('desc')" :class="{ selected: sorting === 'desc' }">Sort Descending</button>
    </div>
    <ul>
      <user-item v-for="user in displayedUsers" :key="user.id" :user-name="user.fullName" :id="user.id"
        @list-projects="$emit('list-projects', $event)"></user-item>
    </ul>
  </base-container>
</template>

<script>
import { toRefs } from 'vue';

import UserItem from './UserItem.vue';
import useSearch from '../../hooks/search';
import useSort from '../../hooks/sort';

export default {
  components: {
    UserItem,
  },
  props: ['users'],
  emits: ['list-projects'],
  setup(props) {
    const { users } = toRefs(props);

    const { availableItems, enteredSearchTerm, updateSearch } = useSearch(users, 'fullName');

    const { sorting, sort, displayedUsers, } = useSort(availableItems, 'fullName');




    return {
      enteredSearchTerm,
      updateSearch,
      displayedUsers,
      sorting,
      sort
    };
  },
};
</script>

<style lang="scss" scoped>
ul {
  padding: 0;
  margin: 0;
  list-style: none;
}

div {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;



  button {
    width: 100%;
    max-width: 100%;

    @media (min-width: 400px) {
      width: calc(50% - 5px);
      max-width: calc(50% - 5px);
    }
  }
}
</style>