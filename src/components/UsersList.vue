<template>
  <div class="users-list">
    <h3>Users</h3>
    <ul class="users-list__list">
      <li
        class="users-list__item card"
        v-for="(user, key) in users"
        :key="key"
        v-on:click="$emit('select-user', user)"
        v-bind:class="{ 'active': user === activeUser }"
      >
        <img :src="user.img" :alt="user.name" class="users-list__image">
        <span class="users-list__name">{{ user.name }}</span>
        <rating :stars="user.rating" class="users-list__rating"/>
      </li>
    </ul>
  </div>
</template>

<script>
import Rating from "./Rating";
import SearchFilter from "./SearchFilter";

export default {
  name: "UsersList",
  components: {
    Rating,
    SearchFilter
  },
  props: {
    users: Array,
    activeUser: Object
  },
  methods: {}
};
</script>

<style scoped lang="scss">
$this: ".users-list";

#{$this} {
  ul {
    list-style-type: none;
    padding: 0;
  }

  &__item {
    padding: 20px 24px;
    display: flex;
    align-items: center;
    transition: all 300ms ease-in;
    cursor: pointer;

    &:hover {
      color: #8181D0;
    }

    &:not(:first-child) {
      margin-top: 12px;
    }

    &.active {
      color: #8181D0;
      background-color: #EFF0FA;
    }
  }

  &__name {
    font-weight: bold;
  }

  &__image {
    border-radius: 50%;
    width: 52px;
    height: 52px;
    margin-right: 12px;
  }

  &__rating {
    margin-left: auto;
  }
}
</style>
