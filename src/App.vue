<template>
  <div id="app">
    <div class="game-area">
      <DeckPile :deck="cardsDeck" @move-to-hand="moveCardToHand" @add-heat="addHeatCard" :extraHeat="extraHeatCards"/>
      <PlayerHand :playerHand="playerHand" @move-to-discard="moveToDiscardPile"/>
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
        { id: 16, value: 'stress' },
        { id: 17, value: 'stress' },
        { id: 18, value: 'stress' }
      ],
      playerHand: [],
      discardPile: [],
      extraHeatCards: [
        { id: 19, value: 'heat' },
        { id: 20, value: 'heat' },
        { id: 21, value: 'heat' },
        { id: 22, value: 'heat' },
        { id: 23, value: 'heat' },
        { id: 24, value: 'heat' },
      ]
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
    },

    moveToDiscardPile(card) {
      const index = this.playerHand.findIndex(c => c.id === card.id);
      if (index !== -1) {
        const [movedCard] = this.playerHand.splice(index, 1);
        this.discardPile.push(movedCard);
      }
    },

    addHeatCard(card) {
      const index = this.extraHeatCards.findIndex(c => c.id === card.id);
      if (index !== -1) {
        const [movedCard] = this.extraHeatCards.splice(index, 1);
        this.discardPile.push(movedCard);
      }
    },
  }

};

</script>

<style>
.game-area {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 80%;
  margin: 5% auto;
}

.game-area > div {
  min-height: 250px;
}
</style>
