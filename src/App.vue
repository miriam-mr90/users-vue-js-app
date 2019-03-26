<template>
  <div id="app">
    <user-preview :user="activeUser" v-if="activeUser != null"/>
    <users-list :users="users" :active-user="activeUser" v-on:select-user="updateSelectedUser"/>
  </div>
</template>

<script>
import usersData from "/users.json";
import UsersList from "./components/UsersList";
import UserPreview from "./components/UserPreview";
import Rating from "./components/Rating";

export default {
  name: "App",
  components: {
    UsersList,
    UserPreview,
    Rating
  },
  data() {
    return {
      users: usersData.people,
      activeUser: null,
      activeUserIndex: null
    };
  },
  methods: {
    updateSelectedUser(user) {
      this.activeUser = user;
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

.card {
  background-color: #FFF;
  border-radius: 4px;
  box-shadow: 0 4px 8px rgba(18, 42, 68, 0.2);
  transition: box-shadow 300ms;
}
</style>
