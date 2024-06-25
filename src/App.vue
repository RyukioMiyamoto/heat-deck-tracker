<template>
  <div id="app">
    <div class="game-area">
      <DeckPile :deck="cardsDeck" @move-to-hand="moveCardToHand" />
      <PlayerHand :playerHand="playerHand" />
      <DiscardPile :discardPile="discardPile" />
    </div>
  </div>
</template>

<script>
import DeckPile from './components/DeckPile.vue';
import DiscardPile from './components/DiscardPile.vue';
import PlayerHand from './components/PlayerHand.vue';

export default {
  name: 'App',
  components: {
    DeckPile,
    PlayerHand,
    DiscardPile
  },
  data() {
    return {
      cardsDeck: [
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
      ],
      playerHand: [],
      discardPile: []
    };
  },

  methods: {
    moveCardToHand(card) {
      if (this.playerHand.length < 7) {
        const index = this.cardsDeck.findIndex(c => c.id === card.id);
        if (index !== -1) {
          const [movedCard] = this.cardsDeck.splice(index, 1);
          this.playerHand.push(movedCard);
        }
      } else {
        console.log('Limite máximo de cartas na mão alcançado.');
      }
    }
  }

};

</script>

<style>
.game-area {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 1000px;
  margin: 5% auto;
}
</style>
