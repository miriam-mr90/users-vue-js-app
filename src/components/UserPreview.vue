<template>
  <div class="user-preview" :id="'id-' + user.id">
    <button class="btn user-preview__close" v-on:click="$emit('select-user', null)">Close
      <font-awesome-icon icon="times" class="btn__ico"/>
    </button>
    <img :src="user.img" :alt="user.name" class="user-preview__image">
    <h2 class="user-preview__title">{{ user.name }}</h2>
    <rating :stars="user.rating" class="user-preview__rating"/>
    <ul class="user-preview__likes">
      <li class="like" v-for="(like, key) in user.likes" :key="key">{{ like }}</li>
    </ul>
    <q class="user-preview__quote">{{ user.quote }}</q>
  </div>
</template>

<script>
import Rating from "./Rating";

export default {
  name: "UsersList",
  components: {
    Rating
  },
  props: {
    user: Object
  },
  methods: {}
};
</script>

<style scoped lang="scss">
$this: ".user-preview";

#{$this} {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-bottom: 30px;
  margin-bottom: 10px;
  border-bottom: 2px dashed #EBECEC;

  &__close {
    margin-left: auto;
    margin-bottom: 20px;
  }

  &__image {
    border-radius: 50%;
    width: 160px;
    height: 160px;
    border: 6px solid #FFF;
    box-shadow: 0 4px 8px rgba(18, 42, 68, 0.2);
  }

  &__title {
    font-size: 32px;
    text-align: center;
    margin-bottom: 6px;
  }

  &__rating {
    margin-bottom: 10px;
  }

  &__quote {
    text-align: center;
  }

  &__likes {
    display: flex;

    .like {
      font-size: 13px;
      background-color: #EFF0FA;
      color: #8181D0;
      padding: 4px 14px;
      border-radius: 12px;
      min-width: max-content;

      &:not(:first-child) {
        margin-left: 12px;
      }
    }
  }
}
</style>