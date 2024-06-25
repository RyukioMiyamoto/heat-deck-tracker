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

    <h3>Cartas Heat e Stress</h3>
    <div class="heat-cards">
      <div
        v-for="card in extraHeat"
        :key="card.id"
        @click="addHeatCard(card)"
        class="card heat-card"
      >
        <CardItem value="+heat" />
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
    },
    extraHeat: {
      type: Array,
      required: true
    }
  },

  methods: {
    moveToPlayerHand(card) {
      this.$emit('move-to-hand', card);
    },
    addHeatCard(card) {
      this.$emit('add-heat', card);
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

.heat-cards {
  margin-top: 20px;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

</style>
