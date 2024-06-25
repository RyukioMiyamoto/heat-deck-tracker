<template>
  <div id="app">
    <div class="card-container">
      <CardItem v-for="card in cards" :key="card.id" :value="card.value" />
    </div>
  </div>
</template>

<script>
import CardItem from './components/CardItem.vue';

export default {
  name: 'App',
  components: {
    CardItem
  },
  data() {
    return {
      cards: [
        { id: 1, value: 1 },
        { id: 2, value: 1 },
        { id: 3, value: 1 },
        { id: 4, value: 2 },
        { id: 5, value: 2 },
        { id: 6, value: 2 },
        { id: 7, value: 3 },
        { id: 8, value: 3 },
        { id: 9, value: 3 },
        { id: 10, value: 4 },
        { id: 11, value: 4 },
        { id: 12, value: 4 },
        { id: 13, value: 5 },
        { id: 14, value: 0 },
        { id: 15, value: 'heat' },
        { id: 16, value: 'stress' }
      ]
    };
  }
};
</script>

<style>
.card-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  width: 80%;
  margin: 10% auto;
}
</style>
