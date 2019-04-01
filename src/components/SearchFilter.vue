<template>
  <div class="search">
    <div class="search__input-group">
      <input
        type="text"
        name="searchfilter"
        placeholder="Search..."
        autocomplete="off"
        class="search__input"
        v-bind:value="searchText"
        v-on:input="$emit('search', $event.target.value)"
      >
      <font-awesome-icon icon="search" class="search__icon"/>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchFilter",
  props: {
    searchText: String
  }
};
</script>

<style scoped lang="scss">
$this: ".search";

#{$this} {
  display: flex;
  justify-content: space-around;
  margin-bottom: 30px;

  &__input-group {
    position: relative;
  }

  &__input {
    width: 300px;
    border-radius: 34px;
    padding-right: 40px;
  }

  &__icon {
    color: #a2a7ae;
    position: absolute;
    right: 16px;
    top: 50%;
    transform: translateY(-50%);
  }
}
</style>