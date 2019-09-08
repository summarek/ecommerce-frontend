<template>
  <md-card>
    <md-card-media>
      <img :src="Item.itemImage" alt="People" />
    </md-card-media>

    <md-card-header>
      <div class="md-title">{{ Item.itemTitle }}</div>
      <div class="md-subtitle">${{ Item.itemPrice }}</div>
    </md-card-header>

    <md-card-expand>
      <md-card-actions md-alignment="space-between">
        <div>
          <md-button class="md-dense md-raised md-primary">Buy now!</md-button>
          <md-button @click="addToBasket" class="md-dense md-raised md-primary"
            >Add to basket</md-button
          >
        </div>

        <md-card-expand-trigger>
          <md-button class="md-icon-button">
            <md-icon
              ><img
                width="20px"
                src="https://img.icons8.com/android/24/000000/down.png"
            /></md-icon>
          </md-button>
        </md-card-expand-trigger>
      </md-card-actions>

      <md-card-expand-content>
        <md-card-content>
          {{ Item.itemDescription }}
        </md-card-content>
      </md-card-expand-content>
    </md-card-expand>
  </md-card>
</template>

<script>
import { EventBus } from "../main";

export default {
  props: {
    Item: {
      type: Object
    }
  },
  methods: {
    addToBasket() {
      EventBus.$emit("addedToBasket", this.Item);
    }
  }
};
</script>

<style lang="scss" scoped></style>
