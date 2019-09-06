<template>
  <div class="home">
    <div class="grid">
      <Item
        class="grid__item"
        v-for="Item in myShopItems"
        :key="Item.itemName"
        :Item="Item"
      ></Item>
    </div>
  </div>
</template>

<script>
import Item from "../components/Item";

export default {
  name: "home",
  props: {
    shopItems: {
      type: Array
    }
  },
  components: {
    Item
  },
  data() {
    return {
      myShopItems: this.shopItems
    };
  },
  mounted() {
    console.log(this.myShopItems);
  }
};
</script>
<style lang="scss" scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, 300px);
  grid-gap: 1rem;
  justify-content: center;
  align-content: center;
  margin-top: 2rem;
}
</style>
