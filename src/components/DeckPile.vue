<template>
  <div class="deck">
    <h2>Pilha de compras</h2>
    <div class="cards">
      <CardItem v-for="card in deck" :key="card.id" :value="card.value" />
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
  }
};
</script>

<style scoped>
.deck {
  margin-bottom: 20px;
}
.cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
