<template>
  <nav class="navigation">
    <router-link class="navigation__link" to="/">Home |</router-link>
    <router-link class="navigation__link" to="/account"
      >Your account</router-link
    >
    <div>
      <md-badge
        class="md-primary"
        md-position="bottom"
        :md-content="shopBasket.length"
      >
        <md-button class="md-icon-button">
          <md-icon><img src="../assets/basket.png" alt="" srcset=""/></md-icon>
        </md-button>
      </md-badge>
    </div>
    <Basket :shopBasket="shopBasket"></Basket>
  </nav>
</template>

<script>
import Basket from "../components/Basket";

export default {
  props: {
    shopBasket: {
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
}
</style>
