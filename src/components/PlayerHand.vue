<template>
  <div class="player-hand">
    <h2>Mão do Jogador</h2>
    <div class="cards">
      <div
        class="card-container"
        v-for="card in playerHand"
        :key="card.id"
        @click="moveToDiscardPile(card)"
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
    playerHand: {
      type: Array,
      required: true
    }
  },
  methods: {
    moveToDiscardPile(card) {
      this.$emit('move-to-discard', card);
    }
  }
};
</script>

<style scoped>
.player-hand {
  margin-top: 20px;
}

.cards {
  display: flex;
  justify-content: center;
}

.card-container {
  width: 100px;
  height: 150px;
  margin: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
</style>
