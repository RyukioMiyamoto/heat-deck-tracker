<template>
  <div class="player-hand">
    <h2>Mão do Jogador</h2>
    <div class="cards">
      <div class="card" v-for="card in playerHand" :key="card.id">
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
</style>
