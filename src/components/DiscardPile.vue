<template>
  <div class="discard-pile">
    <h2>Pilha de Descarte</h2>
    <div class="cards">
      <CardItem v-for="card in discardPile" :key="card.id" :value="card.value" />
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
    discardPile: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.discard-pile {
  margin-top: 20px;
}
.cards {
  display: flex;
  justify-content: center;
}
</style>
