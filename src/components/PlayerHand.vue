<template>
  <div class="hand">
    <h2>Mão do Jogador</h2>
    <div class="cards">
      <CardItem v-for="cardItem in hand" :key="cardItem.id" :value="cardItem.value" />
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
    hand: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.hand {
  margin-top: 20px;
}
.cards {
  display: flex;
  justify-content: center;
}
</style>
