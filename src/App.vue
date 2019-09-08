<template>
  <div id="app">
    <Nav :shopBasket="shopBasket"></Nav>
    <pay-now-modal></pay-now-modal>
    <router-view :shopItems="shopItems" />
  </div>
</template>

<script>
import { EventBus } from "./main";
import Nav from "../src/components/Nav.vue";
import PayNowModal from "../src/components/PayNowModal.vue";
export default {
  components: {
    Nav,
    PayNowModal
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
          itemAmount: 1,
          chosenItemAmount: 1,
          itemId: 1
        },
        {
          itemImage:
            "https://www.razor.com/wp-content/uploads/2018/01/A_CL_Product.png",
          itemTitle: "scooter",
          itemPrice: 1234.12,
          itemDescription: "really nice scooter",
          itemAmount: 3,
          chosenItemAmount: 1,
          itemId: 2
        },
        {
          itemImage:
            "https://www.razor.com/wp-content/uploads/2018/01/A_CL_Product.png",
          itemTitle: "phone",
          itemPrice: 34534,
          itemDescription: "really nice phone",
          itemAmount: 2,
          chosenItemAmount: 1,
          itemId: 3
        },
        {
          itemImage:
            "https://www.razor.com/wp-content/uploads/2018/01/A_CL_Product.png",
          itemTitle: "desk",
          itemPrice: 34,
          itemDescription: "really nice desk",
          itemAmount: 10,
          chosenItemAmount: 1,
          itemId: 4
        }
      ],
      shopBasket: []
    };
  },
  created() {
    EventBus.$on("addedToBasket", data => {
      if (this.shopBasket.indexOf(data) == -1) {
        this.shopBasket.push(data);
      }
    });
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
.modal{
    position: fixed;
    left:0;
    right:0;
    margin-left:auto;
    margin-right:auto;
    top:0;
    bottom:0;
    margin-top:auto;
    margin-bottom:auto;
    z-index: 999;
    width: 80vw;
    height: 80vh;
    background-color: rgba(99, 99, 99, 0.4);
}
</style>
