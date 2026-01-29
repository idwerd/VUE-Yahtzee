<script setup>
import ThrownDice from './components/ThrownDice.vue';
import ScoreTable from './components/ScoreTable.vue';
import {ref} from 'vue';

const dice = ref([0, 0, 0, 0, 0]);
const count = ref({
  1: 0,
  2: 0,
  3: 0,
  4: 0,
  5: 0,
  6: 0,
});
</script>

<template>
  <ThrownDice v-model:diceValues="dice" v-model:count="count" />
  <ScoreTable v-model:diceValues="dice" v-model:count="count" />
</template>

<style scoped></style>
