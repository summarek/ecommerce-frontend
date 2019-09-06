<template>
  <nav class="navigation">
    <router-link class="navigation__link" to="/">Home |</router-link>
    <router-link class="navigation__link" to="/account"
      >Your account</router-link
    >
    <div class="navigation__icon"></div>
    <Basket :shopItems="shopItems"></Basket>
  </nav>
</template>

<script>
import Basket from "../components/Basket";

export default {
  props: {
    shopItems: {
      type: Array
    }
  },
  components: {
    Basket
  }
};
</script>

<style lang="scss" scoped>
.navigation {
  display: flex;
  justify-content: flex-end;

  &__link {
    margin: 0.5rem;
  }
  &__icon {
    background-image: url("../assets/basket.png");
    width: 3rem;
    height: auto;
    background-repeat: no-repeat;
  }
}
</style>
