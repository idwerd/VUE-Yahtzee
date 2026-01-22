<script setup>
import ThrownDice from './components/ThrownDice.vue';
//import ScoreTable from './components/ScoreTable.vue';
import {ref} from 'vue';
//import ScoreTable from './components/ScoreTable.vue';

const dice = ref([]);
console.log(dice.value);
</script>

<template>
  <ThrownDice v-model:dice="dice" />
  <h1>{{ dice }}</h1>
</template>

<style scoped></style>
