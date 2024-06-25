<!-- DeckPile.vue -->
<template>
  <div class="deck-pile">
    <h2>Baralho Total</h2>
    <div class="cards">
      <div
        v-for="card in deck"
        :key="card.id"
        @click="moveToPlayerHand(card)"
        class="card"
      >
        <CardItem :value="card.value" />
      </div>
    </div>
  </div>
</template>

<script>
import CardItem from './CardItem.vue';

export default {
  components: {
    CardItem
  },
  props: {
    deck: {
      type: Array,
      required: true
    }
  },
  methods: {
    moveToPlayerHand(card) {
      this.$emit('move-to-hand', card);
    }
  }
};
</script>

<style scoped>
.deck-pile {
  margin-bottom: 20px;
}
.cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.card {
  cursor: pointer;
}
</style>
