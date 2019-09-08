<template>
  <div class="modal">

  </div>
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
.modal{

}
</style>
