<template>
  <div class="rating">
    <font-awesome-icon
      icon="star"
      class="star rating__item"
      v-for="star in starsArray"
      :class="{ 'rating__item--empty': star.empty }"
      :key="star.id"
    />
  </div>
</template>

<script>
// JS library to use range function
import range from "lodash/range";

export default {
  name: "Rating",
  props: {
    stars: Number
  },
  computed: {
    starsArray() {
      return range(5).map(index => {
        return {
          id: index,
          empty: this.stars <= index
        };
      });
    }
  }
};
</script>

<style scoped lang="scss">
$this: ".rating";

#{$this} {
  &__item {
    color: #F7D034;

    &--empty {
      color: #E3E3E4;
    }
  }
}
</style>
