<template>
  <div class="cards">
    <GameCard
      v-for="(card, index) in cards"
      :key="card"
      :card="card"
      :is-current="index === 0"
      @cardAccepted="$emit('cardAccepted');"
      @cardRejected="$emit('cardRejected');"
      @cardSkipped="$emit('cardSkipped');"
      @hideCard="$emit('hideCard');"
    />
  </div>
</template>

<script>
import GameCard from "@/components/GameCard";

export default {
  components: {
    GameCard
  },

  props: {
    cards: {
      type: Array,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
.cards {
position: relative;
    display: flex;
    /* margin: 50px; */
    width: calc(100vw - 16px);
    /* height: calc(100vh - 32px); */
    align-items: center;
}
</style>
