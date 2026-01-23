<script setup>
import ThrownDice from './components/ThrownDice.vue';
//import ScoreTable from './components/ScoreTable.vue';
//import {ref} from 'vue';
//import ScoreTable from './components/ScoreTable.vue';

//const dice = ref([]);
</script>

<template>
  <ThrownDice v-model="countModel" />
</template>

<style scoped></style>
