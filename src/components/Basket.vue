<template>
  <div>
    <md-table v-model="shopItems" md-card>
      <md-table-toolbar>
        <h1 class="md-title">Your basket</h1>
      </md-table-toolbar>

      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Amount" md-numeric>
          <div class="md-layout-item">
            <md-field>
              <md-select
                v-model="item.itemAmount"
                name="Amount"
                id="Amount"
                placeholder="Amount"
              >
                <md-option value="1">1</md-option>
                <md-option value="2">2</md-option>
                <md-option value="3">3</md-option>
                <md-option value="4">4</md-option>
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
        <md-table-cell md-label="Price" md-sort-by="price"
          >${{ item.itemPrice }}</md-table-cell
        >
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
export default {
  props: {
    shopItems: {
      type: Array
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
