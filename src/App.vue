<template>
  <div id="app">
    <div class="aside" v-bind:class="{ 'aside--expanded': activeUser === null }">
      <h3>Users</h3>
      <search-filter :search-text="searchText" v-on:search="search"/>
      <users-list
        :users="usersFiltered"
        :active-user="activeUser"
        v-on:select-user="updateSelectedUser"
      />
    </div>
    <div class="main">
      <user-preview
        :user="activeUser"
        v-if="activeUser != null"
        v-on:select-user="updateSelectedUser"
      />
    </div>
  </div>
</template>

<script>
import usersData from "/users.json";
import UsersList from "./components/UsersList";
import UserPreview from "./components/UserPreview";
import Rating from "./components/Rating";
import SearchFilter from "./components/SearchFilter";

export default {
  name: "App",
  components: {
    UsersList,
    UserPreview,
    Rating,
    SearchFilter
  },
  data() {
    return {
      users: usersData.people,
      activeUser: null,
      searchText: null
    };
  },
  methods: {
    updateSelectedUser(user) {
      this.activeUser = user;
    },
    search(text) {
      this.searchText = text.toLowerCase().trim();
    }
  },
  computed: {
    usersFiltered() {
      if (!this.searchText) return this.users;
      return this.users.filter(
        c => c.name.toLowerCase().indexOf(this.searchText) > -1
      );
    }
  }
};
</script>

<style lang="scss">
body {
  background: #fafbfc;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: #4e5357;
  display: flex;
  flex-wrap: nowrap;
  width: 80vw;
  //max-width: 620px;
  margin-left: auto;
  margin-right: auto;
  padding-top: 30px;
}

h3 {
  text-align: center;
}

ul {
  list-style-type: none;
  padding: 0;
}

input {
  min-height: 36px;
  padding: 4px 12px;
  box-sizing: border-box;
  outline: none;
  border: 1px solid #EBECEC;
  border-radius: 34px;
  font-size: 14px;

  &::placeholder {
    color: #D6DADA;
    opacity: 1;
  }

  &:focus,
  &:active,
  &:hover {
    border-color: #D6DADA;
    color: #a2a7ae;
  }
}

button {
  border: none;
  margin: 0;
  padding: 0;
  width: auto;
  overflow: visible;
  background: transparent;
  color: inherit;
  font: inherit;
  line-height: normal;
  -webkit-font-smoothing: inherit;
  -moz-osx-font-smoothing: inherit;
  -webkit-appearance: none;

  &::-moz-focus-inner {
    border: 0;
    padding: 0;
  }
}

.aside {
  width: 40%;
  transition: width 300ms linear;

  &--expanded {
    min-width: max-content;
    width: 100%;

    & + .main {
      width: 0;
      padding-left: 0;
    }
  }
}

.main {
  width: 60%;
  padding-left: 30px;
}

.card {
  background-color: #FFF;
  border-radius: 4px;
  box-shadow: 0 4px 8px rgba(18, 42, 68, 0.2);
  transition: box-shadow 300ms;
}

.btn {
  display: flex;
  align-items: center;
  padding: 6px 16px;
  border-radius: 4px;
  background: #00B6C8;
  color: #FFF;
  font-size: 14px;
  cursor: pointer;

  &__ico {
    margin-left: 8px;
  }
}
</style>
