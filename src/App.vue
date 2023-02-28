<template>
  <main>
    <user-list :users="activeUsers" @list-projects="selectUser"></user-list>
    <projects-list :user="selectedUser"></projects-list>
  </main>
</template>

<script>
import USER_DATA from './dummy-data.js';

import UserList from './components/users/UserList.vue';
import ProjectsList from './components/projects/ProjectsList.vue';

export default {
  components: {
    UserList,
    ProjectsList,
  },
  data() {
    return {
      selectedUser: null,
      activeUsers: USER_DATA,
    };
  },
  methods: {
    selectUser(uid) {
      this.selectedUser = this.activeUsers.find((usr) => usr.id === uid);
    },
  },
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

main {
  display: flex;
  justify-content: space-around;
  flex-direction: column;

  @media (min-width: 768px) {
    flex-direction: row;
  }
}

button {
  display: inline-block;
  padding: 0.75rem 1.5rem;
  margin: 0.5rem 0;
  border: 1px solid #35495e;
  color: #fff;
  font: inherit;
  font-weight: 700;
  text-decoration: none;
  background-color: #35495e;
  cursor: pointer;

  &:hover,
  &:active,
  &:focus {
    color: #35495e;
    border-color: #42b883;
    background-color: #42b883;
    outline-color: #35495e;
  }

  &:focus {
    outline: 2px solid webkit-focus-ring-color;
    outline-offset: -2px;
  }

  &.selected {
    background-color: #42b883;
    color: #35495e;
    border-color: #42b883;
  }
}
</style>