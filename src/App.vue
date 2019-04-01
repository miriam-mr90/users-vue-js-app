<template>
  <div id="app">
    <search-filter :search-text="searchText" v-on:search="search"/>
    <user-preview :user="activeUser" v-if="activeUser != null"/>
    <users-list
      :users="usersFiltered"
      :active-user="activeUser"
      v-on:select-user="updateSelectedUser"
    />
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
  flex-direction: column;
  width: 80vw;
  max-width: 620px;
  margin-left: auto;
  margin-right: auto;
  padding-top: 30px;
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

.card {
  background-color: #FFF;
  border-radius: 4px;
  box-shadow: 0 4px 8px rgba(18, 42, 68, 0.2);
  transition: box-shadow 300ms;
}
</style>
