<template>
  <div class="rating">
    <font-awesome-icon
      icon="star"
      class="star rating__item"
      v-for="(star, key) in stars"
      :key="key"
    />
    <font-awesome-icon
      icon="star"
      class="star rating__item rating__item--empty"
      v-for="(star, index) in (5 - stars)"
      :key="index"
    />
  </div>
</template>

<script>
export default {
  name: "Rating",
  props: {
    stars: Number
  },
  methods: {}
};
</script>

<style scoped lang="scss">
$this: ".rating";

#{$this} {
  &__item {
    color: #F7D034;
  }

  &__item--empty {
    color: #E3E3E4;
  }
}
</style>
