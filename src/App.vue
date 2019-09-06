<template>
  <div id="app">
    <Nav :shopItems="shopItems"></Nav>
    <router-view :shopItems="shopItems" />
  </div>
</template>

<script>
import Nav from "../src/components/Nav.vue";
export default {
  components: {
    Nav
  },
  data() {
    return {
      shopItems: [
        {
          itemImage:
            "https://4.imimg.com/data4/CO/YS/MY-29352968/samsung-desktop-computer-500x500.jpg",
          itemTitle: "computer",
          itemPrice: 2000,
          itemDescription: "really nice computer",
          itemAmount: 1
        },
        {
          itemImage:
            "https://www.razor.com/wp-content/uploads/2018/01/A_CL_Product.png",
          itemTitle: "scooter",
          itemPrice: 1234,
          itemDescription: "really nice scooter",
          itemAmount: 3
        },
        {
          itemImage:
            "https://www.razor.com/wp-content/uploads/2018/01/A_CL_Product.png",
          itemTitle: "phone",
          itemPrice: 34534,
          itemDescription: "really nice phone",
          itemAmount: 2
        },
        {
          itemImage:
            "https://www.razor.com/wp-content/uploads/2018/01/A_CL_Product.png",
          itemTitle: "desk",
          itemPrice: 34,
          itemDescription: "really nice desk",
          itemAmount: 1
        }
      ]
    };
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Poppins&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
</style>
