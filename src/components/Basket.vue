<template>
  <div>
    <md-toolbar
      md-elevation="0"
      v-if="shopBasket.length == 0"
      class="md-accent"
    >
      <h3 class="md-title">Your basket is empty</h3>
    </md-toolbar>

    <md-toolbar
      md-elevation="0"
      v-if="shopBasket.length > 0"
      class="md-primary"
    >
      <h3 class="md-title">Your basket: {{ shopBasket.length }}</h3>
    </md-toolbar>

    <md-table v-model="shopBasket" md-card>
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Amount" md-numeric>
          <div class="md-layout-item">
            <md-field>
              <md-select
                v-model="item.chosenItemAmount"
                name="Amount"
                id="Amount"
                placeholder="Amount"
              >
                <md-option
                  v-for="amount in item.itemAmount"
                  :key="amount"
                  :value="amount"
                  >{{ amount }}</md-option
                >
              </md-select>
            </md-field>
          </div>
        </md-table-cell>
        <md-table-cell md-label="Title" md-sort-by="title">{{
          item.itemTitle
        }}</md-table-cell>
        <md-table-cell md-label="Description" md-sort-by="description">{{
          item.itemDescription
        }}</md-table-cell>
        <md-table-cell md-label="Price" md-sort-by="price">
          ${{ Math.ceil(item.itemPrice * item.chosenItemAmount * 100) / 100 }}
        </md-table-cell>
        <md-table-cell md-numeric md-label="Delete">
          <img
            @click="deleteItem(item)"
            width="30"
            src="https://img.icons8.com/ios/50/000000/delete-forever.png"
          />
        </md-table-cell>
      </md-table-row>
    </md-table>
    <md-toolbar class="md-accent" md-elevation="1">
      <h3 class="md-title" style="flex: 1">Summary:</h3>
      <md-button class="md-primary">PAY NOW</md-button>
      <md-button>${{ countFullPrice }}</md-button>
    </md-toolbar>
  </div>
</template>

<script>
import { EventBus } from "../main";

export default {
  props: {
    shopBasket: {
      type: Array
    }
  },
  data() {
    return {
      basketFullPrice: null
    };
  },
  methods: {
    deleteItem(item) {
      this.shopBasket.splice(this.shopBasket.indexOf(item), 1);
    }
  },
  created() {
    EventBus.$on("addedToBasket", data => {
      if (this.shopBasket.indexOf(data) == -1) {
        this.shopBasket.push(data);
      }
    });
  },
  computed: {
    countFullPrice: function() {
      return this.shopBasket.reduce(
        (carry, item) => carry + item.itemPrice * item.chosenItemAmount,
        0
      );
    }
  }
};
</script>

<style lang="scss">
.md-layout-item {
  width: 50px;
}
.md-menu-content.md-select-menu {
  width: 10% !important;
}
</style>
