<script setup>
import ThrownDice from './components/ThrownDice.vue';
import ScoreTable from './components/ScoreTable.vue';
import {ref} from 'vue';

const dice = ref([0, 0, 0, 0, 0]);
</script>

<template>
  <ThrownDice v-model="dice" />
  <ScoreTable v-model="dice" />
</template>

<style scoped></style>
