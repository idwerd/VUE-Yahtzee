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

const diceValues = defineModel();
function rollDice() {
  for (let i = 0; i < 5; i++) {
    let randomNumber = Math.floor(Math.random() * 6 + 1);
    diceValues.value[i] = randomNumber;
  }
}
</script>

<template>
  <section id="yahtzee">
    <table class="scoreblok">
      <thead>
        <th colspan="5"><h2>Worp</h2></th>
      </thead>
      <tr>
        <td class="dice" v-for="(die, index) in diceValues" :key="index">{{ die }}</td>
      </tr>
    </table>
    <button id="throw-button" @click="rollDice">Gooien!</button>
  </section>
</template>

<style scoped></style>
