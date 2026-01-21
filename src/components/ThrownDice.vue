<script setup>
/*
Dit component is verantwoordelijk voor het tonen van de 
vijf gegooide dobbelstenen op het scherm en bevat ook de 
knop waarmee je de dobbelstenen kunt gooien. 
Alle logica voor het gooien en weergeven van de dobbelstenen 
bevindt zich in dit component. Gebruik een v-model om de 
gegooide dobbelstenen (array dice ) in App.vue door te geven 
aan ThrownDice .
*/

import {reactive} from 'vue';

let diceValues = reactive([]);
const count = {
  1: 0,
  2: 0,
  3: 0,
  4: 0,
  5: 0,
  6: 0,
};

const rollDice = () => {
  for (let dice in count) {
    count[dice] = 0;
  }

  
  for (let i = 0; i < 5; i++) {
    diceValues[i] = Math.floor(Math.random() * 6 + 1);
    countThrows(diceValues[i]);
  }
};

const countThrows = currentValue => {
  count[currentValue]++;
};

</script>

<template>
  <table>
    <thead>
        <th colspan="5"><h2>Worp</h2></th>
    </thead>
    <tr>
        <td class="dice" v-for="dice, index in diceValues" :key="index" >{{ dice }} </td>
    </tr>
  </table>
  <button @click="rollDice">Gooi!</button>
</template>

<style scoped></style>
